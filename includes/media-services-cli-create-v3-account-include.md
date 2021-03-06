---
title: include file
description: include file
services: media-services
author: Juliako
ms.service: media-services
ms.topic: include
ms.date: 04/13/2018
ms.author: juliako
ms.custom: include file
---

## Create a Media Services account

You first need to create a Media Services account. This section shows what you need for the acount creation using CLI 2.0.

### Create a resource group

Create a resource group using the following command. An Azure resource group is a logical container into which resources like Azure Media Services accounts and the associated Storage accounts are deployed and managed.

```azurecli-interactive
az group create --name amsResourceGroup --location westus2
```

### Create a storage account

When creating a Media Services account, you need to supply the name of an Azure Storage account resource. The specified storage account is attached to your Media Services account. 

You must have one **Primary** storage account and you can have  any number of **Secondary** storage accounts associated with your Media Services account. Media Services supports **General-purpose v2** (GPv2) or **General-purpose v1** (GPv1) accounts. Blob only accounts are not allowed as **Primary**. If you want to learn more about storage accounts, see [Azure Storage account options](../articles/storage/common/storage-account-options.md). 

For more information about how storage accounts are used in Media Services, see [Storage accounts](../articles/media-services/latest/storage-account-concept.md).

The following command creates a Storage account that is going to be associated with the Media Services account. In the script below, you can substitute `storageaccountforams` with your value. The account name must have length less than 24.

```azurecli-interactive
az storage account create --name storageaccountforams \  
--kind StorageV2 \
--sku Standard_RAGRS \
--resource-group amsResourceGroup
```

### Create a Media Services account

The following Azure CLI command creates a new Media Services account. You can replace the following values: `amsaccount`  `storageaccountforams` (must match the value you gave for your storage account), and `amsResourceGroup` (must match the value you gave for the resource group).

```azurecli-interactive
az ams account create --name amsaccount --resource-group amsResourceGroup --storage-account storageaccountforams
```
