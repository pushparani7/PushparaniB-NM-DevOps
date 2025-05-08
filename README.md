# Disaster Recovery and Backup Strategy for Containerized Applications

## Overview
This project sets up a disaster recovery and backup system using Velero for Kubernetes-based applications. It also includes Prometheus for monitoring Velero.

## Requirements
- Kubernetes Cluster
- Velero CLI
- Prometheus

## Deployment Instructions

### 1. Setup Namespace and Application
```bash
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/deployment.yaml
```

### 2. Install Velero
Install Velero with a supported plugin (e.g., AWS, Azure, GCP):
```bash
velero install --provider <PROVIDER> --bucket <BUCKET_NAME> --secret-file <CREDENTIALS_FILE> --backup-location-config <CONFIG>
```

### 3. Backup Application
```bash
./scripts/backup.sh
```

### 4. Restore Application
```bash
./scripts/restore.sh
```

### 5. Monitor with Prometheus
Deploy Prometheus with the config in `monitoring/prometheus-config.yaml`.
