



# Running FastAPI with Hugging FaceRunning FastAPI with Hugging Face

The detail will be in https://github.com/pandapanda3/huggingface-ghcr



# Create Service Principal

## Install Azure CLI
`pip install azure-cli`

`az --version`

## Login
`az login`

## Check cureent subscription
`az account show
`
## Get the subscriptionId 
`az account list --output table
`

## create a service principal in Azure and assign it a specific role with defined scope

Use the following command to obtain `AZURE_APP_ID`, `AZURE_PASSWORD`, and `AZURE_TENANT`:

```bash
az ad sp create-for-rbac --name "my-ml-service-principal" --role Contributor --scopes /subscriptions/04c1b27c-fcd8-43ba-96a2-cfe04a58d0a5
```

- **`az ad sp create-for-rbac`**:
  - This part of the command is telling Azure to create a **service principal (SP)** that can be used for **role-based access control (RBAC)**.
  - A service principal is an identity used by applications or automation tools to access Azure resources.

- **`--name "my-ml-service-principal"`**:
  - This specifies the name of the service principal you are creating. In this case, it’s set to `"my-ml-service-principal"`.
  - The name is primarily for identification purposes, allowing you to recognize and manage this SP among others.

- **`--role Contributor`**:
  - This assigns the **Contributor** role to the service principal.
  - The Contributor role provides read and write permissions on resources within the specified scope. However, it does not allow the SP to manage access (i.e., assign roles to others).
  - This role is often used when you want an application to be able to manage resources but not change access policies.

- **`--scopes /subscriptions/04c1b27c-fcd8-43ba-96a2-cfe04a58d0a5`**:
  - This defines the **scope** of the SP's permissions.
  - In this case, the scope is the entire Azure subscription identified by the subscription ID `04c1b27c-fcd8-43ba-96a2-cfe04a58d0a5`.
  - By setting the scope to this subscription, you are allowing the service principal to access and manage resources within this subscription.