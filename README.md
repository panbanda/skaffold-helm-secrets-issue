Repo shows the issue with render vs up with skaffold

```
# Install SOPS sample gpg key
gpg --import pgp/sops_test_key.asc

# Encrypted with 
sops -e -i secrets.yaml

# Decrypted with 
sops -d -i secrets.yaml

# Skaffold dev puts the secret in container decrypted
# ie: test
skaffold dev

# Skaffold render creates a kube secret manifest with encrypted string
# ie: ENC[AES256_GCM,data:SyyH6w==,iv:CbNC...
skaffold render
```