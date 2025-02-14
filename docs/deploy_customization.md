
# Getting Started with Agents Using Azure AI Foundry: Deployment customization

This document describes how to customize the deployment of the Agents Chat with Azure AI Foundry. Once you follow the steps here, you can run `azd up` as described in the [Deploying](./README.md#deploying) steps.

* [Disabling resources](#disabling-resources)
* [Customizing resource names](#customizing-resource-names)
* [Customizing model deployments](#customizing-model-deployments)

## Disabling resources

Disabling a resource will stop that resource from being created and deployed to your Azure Project. 

* To disable AI Search, run `azd env set USE_SEARCH_SERVICE false`
* To disable Application Insights, run `azd env set USE_APPLICATION_INSIGHTS false`
* To disable Container Registry, run `azd env set USE_CONTAINER_REGISTRY false`

Once you disable these resources, they will not be deployed when you run `azd up`.

## Customizing resource names

By default, this template will use a naming convention with unique strings to prevent naming collisions within Azure.
To override default naming conventions, the following keys can be set:

* `AZURE_AIHUB_NAME` - The name of the AI Foundry Hub resource
* `AZURE_AIPROJECT_NAME` - The name of the AI Foundry Project
* `AZURE_AIENDPOINT_NAME` - The name of the AI Foundry online endpoint used for deployments
* `AZURE_AISERVICES_NAME` - The name of the Azure AI service
* `AZURE_SEARCH_SERVICE_NAME` - The name of the Azure Search service
* `AZURE_STORAGE_ACCOUNT_NAME` - The name of the Storage Account
* `AZURE_KEYVAULT_NAME` - The name of the Key Vault
* `AZURE_CONTAINER_REGISTRY_NAME` - The name of the container registry
* `AZURE_APPLICATION_INSIGHTS_NAME` - The name of the Application Insights instance
* `AZURE_LOG_ANALYTICS_WORKSPACE_NAME` - The name of the Log Analytics workspace used by Application Insights

To override any of those resource names, run `azd env set <key> <value>` before running `azd up`.

## Customizing model deployments

For more information on the Azure OpenAI models and non-Microsoft models that can be used in your deployment, view the [list of models supported by Azure AI Agent Service](https://learn.microsoft.com/azure/ai-services/agents/concepts/model-region-support)

To customize the model deployments, you can set the following environment variables:

### Using a different chat model

Change the chat deployment name:

```shell
azd env set AZURE_AI_CHAT_DEPLOYMENT_NAME Phi-3.5-MoE-instruct
```

Change the chat model format (either OpenAI or Microsoft):

```shell
azd env set AZURE_AI_CHAT_MODEL_FORMAT Microsoft
```

Change the chat model name:

```shell
azd env set AZURE_AI_CHAT_MODEL_NAME Phi-3.5-MoE-instruct
```

Set the version of the chat model:

```shell
azd env set AZURE_AI_CHAT_MODEL_VERSION 2
```

### Setting capacity and deployment SKU

For quota regions, you may find yourself needing to modify the default capacity and deployment SKU. The default tokens per minute deployed in this template is 50,000. 

Change the capacity (in thousands of tokens per minute) of the chat deployment:

```shell
azd env set AZURE_AI_CHAT_DEPLOYMENT_CAPACITY 50
```

Change the SKU of the chat deployment:

```shell
azd env set AZURE_AI_CHAT_DEPLOYMENT_SKU Standard
```

Change the capacity (in thousands of tokens per minute) of the embeddings deployment:

```shell
azd env set AZURE_AI_EMBED_DEPLOYMENT_CAPACITY 50
```

Change the SKU of the embeddings deployment:

```shell
azd env set AZURE_AI_EMBED_DEPLOYMENT_SKU Standard
```
