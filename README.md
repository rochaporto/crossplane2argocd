# crossplane2argocd

This is a very hacky solution to a problem you might not have, or maybe you do
and this is somehow helpful.

Read below...

## Why

Crossplane is a great way to manage any type of cloud resource inside
Kubernetes, including managed clusters in GKE, AKS or EKS.

ArgoCD is a popular GitOps tool that allows declarative definitions of
resources and handles reconciliation in one or several clusters.

What if you want to:
* declare Kubernetes clusters to be created and managed by ArgoCD
* declare a set of services that should run in one or more of the clusters above

ArgoCD assumes you have registered your clusters using:
```
argocd cluster add --name *clustername* *clustercontext*
```

This repo shows a way to automatically discover clusters being managed by
ArgoCD and register them in the same ArgoCD instance, so they can be referenced
in other manifests. It includes the required step of fetching the cluster
credentials using the appropriate cloud provider APIs.

## Requirements

* A secret with credentials to use the cloud provider API/CLI
* This tool must be run in the same cluster as the ArgoCD instance

## Support

* Google GKE: done
* Azure AKS: work in progress
* Amazon EKS: work in progress
* OpenStack: work in progress
