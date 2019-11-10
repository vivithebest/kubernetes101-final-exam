# kubernetes101-final-exam

### Prepare
* create k8s namespace such as prod uat dev
* create docker image registry and replace the `image.registry` value in the helm `values.yaml` file

### For prod env
* install the chart
```shell
helm install dockercoins-prod/ --name dockercoins-prod --namespace prod
```

* upgrade the chart
```shell
helm upgrade dockercoins-prod dockercoins-prod/
```

* delete the chart
```shell
helm delete dockercoins-prod --purge
```

### For dev or uat env
> deploy the single k8s resource like follow command, you can replace the resource or env
* for hasher 
```shell
helm install dockercoins --name dev-hasher --namespace dev --set servicename=hasher --set image.tag=v0.1 --set environment=dev --set service.enabled=true --set healthcheck.enabled=false
```
* for rng
```shell
helm install dockercoins --name dev-rng --namespace dev --set servicename=rng --set image.tag=v0.1 --set environment=dev --set service.enabled=true --set healthcheck.enabled=false
```
* for redis 
```shell
helm install dockercoins --name dev-redis --namespace dev --set servicename=redis --set environment=dev --set service.enabled=true
```
* for worker 
```shell
helm install dockercoins --name dev-worker --namespace dev --set servicename=worker --set image.tag=v0.1 --set environment=dev
```
* for webui
```shell
helm install dockercoins --name dev-webui --namespace dev --set servicename=webui --set image.tag=v0.1 --set environment=dev --set service.enabled=true --set ingress.enabled=true
```