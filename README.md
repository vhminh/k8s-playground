# k8s-playground

A local Kubernetes playground using [kind](https://kind.sigs.k8s.io/)

## Setup

1. Install [mise](https://mise.jdx.dev/getting-started.html)
2. [Activate mise](https://mise.jdx.dev/getting-started.html#activate-mise) by adding the following to your shell rc file:
```sh
# ~/.zshrc
eval "$(mise activate zsh)"
```
> **Note:** If you don't want to activate mise globally, you can prefix commands with `mise exec --` instead, e.g. `mise exec -- kubectl get pods`.

3. Install tools (kind, kubectl):
```sh
mise install
```

## Usage

### Manage cluster

List available tasks:
```sh
mise tasks
```

Create a cluster:
```sh
mise run create
```

Apply k8s resource manifests:
```sh
mise run apply
```

Delete a cluster:
```sh
mise run delete
```

### ArgoCD

Port-forward the ArgoCD server:
```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Access the UI at https://localhost:8080

Get the initial admin password:
```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
