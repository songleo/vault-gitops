# Vault

Deploy Vault via OpenShift GitOps.

## Post-install

- Initialized and unsealed Vault

- Ignore the `caBundle` field of `MutatingWebhookConfiguration`

Need to configure argo to ignore the `caBundle` field of `MutatingWebhookConfiguration` webhooks:

```
data:
  resource.customizations: |
    admissionregistration.k8s.io/MutatingWebhookConfiguration:
      ignoreDifferences: |
        jsonPointers:
        - /webhooks/0/clientConfig/caBundle
```

For more information, see [Diffing Customization](https://argo-cd-docs.readthedocs.io/en/latest/user-guide/diffing/#system-level-configuration).
