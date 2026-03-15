# oci-talos-gitops-apps

Argo CD GitOps applications for the OCI free-tier Talos cluster (4× Ampere A1.Flex).

Managed by [omni-oci-proxmox](https://github.com/syscode-labs/omni-oci-proxmox) via Omni SideroLink.

## Bootstrap

Argo CD and Cilium are bootstrapped via Talos `cluster.inlineManifests` — no manual install step.
On first boot, the root App-of-Apps in `bootstrap/` is applied automatically.

## Structure

```
bootstrap/          Application CRDs — Argo CD syncs these on startup
infrastructure/     Helm values and configs per app
```

## Adding an app

1. Add an `Application` CRD to `bootstrap/<app-name>.yaml`
2. Add config/values to `infrastructure/<app-name>/`
3. Commit — Argo CD auto-syncs
