# Deploy Heimdall with Acorn
Install Heimdall with Acorn.

## Pre-requisites
- A Kubernetes cluster
- An NFS shared directory
- [Install Acorn CLI](https://docs.acorn.io/installation/installing#acorn-cli)
- [Install Acorn on Kubernetes cluster](https://docs.acorn.io/installation/installing#installing-acorn-onto-kubernetes-clusters)

## Update NFS share details in PV & SC
```
$ sed -i 's/NFS_SERVER_IP/<YOUR_NFS_SERVER_IP>/g' {sc.yaml,pv.yaml}
$ sed -i 's/HEIMDALL_CONF_NFS_PATH/<CONF_DIR_PATH_ON_SERVER>/g' {sc.yaml,pv.yaml}
```

## Create PV & SC in your Kubernetes cluster
```
$ kubectl create -f pv.yaml -f sc.yaml
```

# Run Acorn App
```
$ Acorn run -n heimdall .
```
