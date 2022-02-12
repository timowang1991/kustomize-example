# Prerequisites
* [kustomize](https://kubectl.docs.kubernetes.io/installation/kustomize/) installed or docker installed

<br/>

# What is this?
* A command tool to override k8s object yaml config based on the same `metadata.name` in each file under the `overlays/` directory.

<br/>

# How to run

* kustomize command
```bash
kustomize build base/

# Generate staging k8s object yaml config
kustomize build overlays/staging

# Generate prod k8s object yaml config
kustomize build overlays/production
```

* using docker
```bash
docker run --rm -v $(pwd):/src k8s.gcr.io/kustomize/kustomize:v3.8.7 build /src/base
docker run --rm -v $(pwd):/src k8s.gcr.io/kustomize/kustomize:v3.8.7 build /src/overlays/staging
docker run --rm -v $(pwd):/src k8s.gcr.io/kustomize/kustomize:v3.8.7 build /src/overlays/production
```

<br/>

# Recommended folder structure
```
.
├── base
│   ├── configMap.yaml
│   ├── deployment.yaml
│   ├── kustomization.yaml
│   └── service.yaml
└── overlays
    ├── production
    │   ├── deployment.yaml
    │   └── kustomization.yaml
    └── staging
        ├── kustomization.yaml
        └── map.yaml
```