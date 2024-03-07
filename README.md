# AKS with Pulumi and Python

## Python set up

- For Python, I'm using `venv` for the environment. As a reminder, the setup for this is: `python3 -m venv .venv`

To activate it: `source .venv/bin/activate`

Once activated the terminal prompt will typically show `(.venv)`

## Pulumi

For this project we're using the latest, best way to work with Azure. That's the `Azure Native` provider. To use this with Python, we need to import it and use it like so:

```
import pulumi_azure_native as azure_native

resource_group = azure_native.resources.ResourceGroup("resourceGroup")
```

## Authentication

It looks like Pulumi can authenticate to Azure using:

- Azure CLI
- OpenID Connect (OIDC)
- Service Principal with a client secret or cert
- Managed Service Identity

Because it's just me working on this project, I'm going with the Azure CLI. However, if I were working with a team, I'd probably use the MSI. And for GitHub, my favorite is OpenID. I'm keeping it simple for now and going with the CLI

How is that done?

I'm also using Codespaces for most of my development, so I'll go with the device code option.

```
az login --use-device-code
```

I just tried this and discovered I don't have the AZ CLI installed. So I'll install it, and probably udate my devcontainer.json to include it in the future. I believe I can do that by going into customizations and adding this line

```
"ms-vscode.azurecli"
```
