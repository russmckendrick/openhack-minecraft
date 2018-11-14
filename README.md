# OpenHack Minecraft Stuff

## Create the storeage

```
$ az aks show --resource-group hackAKS --name hackAKSCluster --query nodeResourceGroup -o tsv
$ az storage account create --resource-group MC_hackAKS_hackAKSCluster_eastus --name hackakscluster --sku Standard_LRS
```

## Launch the stuff

```
kubectl create namespace mincraftns
kubectl -n mincraftns apply -f ~/Desktop/mine-sc.yaml
kubectl -n mincraftns apply -f ~/Desktop/mine-store-roles.yaml
kubectl -n mincraftns apply -f ~/Desktop/mine-store-claim.yaml
kubectl -n mincraftns get pvc azurefile
kubectl -n mincraftns apply -f ~/Desktop/minecraft.yaml
kubectl -n mincraftns get pods
kubectl -n mincraftns get deployments
kubectl -n mincraftns expose deployment minecraft-deployment --type=LoadBalancer --name=minecraft-lb
kubectl -n mincraftns describe services minecraft-lb
```

## Misc

```
kubectl delete namespace mincraftns
```