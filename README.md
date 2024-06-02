# azure-deploy-stack

デプロイスタックのお勉強。


## IAM の追加

denyDelete, denyWriteAndDelete の設定をするための権限を付与する。

```bash
az role assignment create --role 'Azure Deployment Stack Owner' --assignee <user id> --scope <resource group id>
```



## デプロイスタックの作成

子リソースも含めて変更、削除を禁止する。

```bash
az stack group create --name 'stack-1' --resource-group 'deploy-stack' --template-file '1-vnet.bicep' --action-on-unmanage 'detachAll' --deny-settings-mode 'denyWriteAndDelete' --cs
```


## 削除

リソースも削除。

```bash
az stack group delete --name stack-1 --resource-group deploy-stack --action-on-unmanage deleteResources
```
