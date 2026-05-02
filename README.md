# Kubernetes manifests for PediNephro

This directory contains Kubernetes manifests for the PediNephro environment.

## Files
- `00-namespace.yaml` - creates the `pedinephro` namespace
- `01-secrets.yaml` - Docker registry and application secrets
- `02-configmap.yaml` - shared environment values
- `03-mysql.yaml` - MySQL deployment and service
- `04-eureka.yaml` - Eureka deployment and service
- `05-keycloak.yaml` - Keycloak deployment and service
- `06-user-service.yaml` - user-service deployment and service
- `07-medical-records.yaml` - medical-records deployment and service
- `08-transplant-service.yaml` - transplant-service deployment and service
- `09-vital-signs-service.yaml` - vital-signs-service deployment and service
- `10-frontend.yaml` - frontend deployment and service
- `11-ingress.yaml` - ingress routes for frontend and API

## Apply manifests
Run from the machine that has `kubectl` configured for the target cluster:

```bash
kubectl apply -f k8s/00-namespace.yaml
kubectl apply -f k8s/01-secrets.yaml
kubectl apply -f k8s/02-configmap.yaml
kubectl apply -f k8s/03-mysql.yaml
kubectl apply -f k8s/04-eureka.yaml
kubectl apply -f k8s/05-keycloak.yaml
kubectl apply -f k8s/06-user-service.yaml
kubectl apply -f k8s/07-medical-records.yaml
kubectl apply -f k8s/08-transplant-service.yaml
kubectl apply -f k8s/09-vital-signs-service.yaml
kubectl apply -f k8s/10-frontend.yaml
kubectl apply -f k8s/11-ingress.yaml
```

## Notes
- Replace the secret values in `01-secrets.yaml` before applying.
- The manifests use Docker Hub images under `azizos07/*`.
- If your cluster is local and cannot pull public Docker Hub images, use `kind load docker-image` or push the images to a registry accessible from the cluster.
