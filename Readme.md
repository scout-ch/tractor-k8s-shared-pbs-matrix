# PBS-Matrix

This repo contains the deployment config for Element Server Suite Community, which is an implementation of a Chat Service based on Matrix Protocol.

## Deployment

Deployment is done automatically via FluxCD. See https://github.com/scout-ch/tractor-k8s-shared

On first install, some secrets need to be created manually (or externally) into the existing namespace. You can use the secrets.yml file as a template for this.

## Update/Install

> [!IMPORTANT]  
> This was used for initial installation, now we use FluxCD for automated updates and deployment.

```bash
kubectl apply -f secrets.yml
# Edit secrets to have content
helm upgrade --install --namespace "pbs-matrix" ess oci://ghcr.io/element-hq/ess-helm/matrix-stack -f values.yml --wait
```