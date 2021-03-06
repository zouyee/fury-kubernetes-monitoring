# Alertmanager Operated

Alertmanager handles alerts sent by Prometheus server and routes them to
configured receiver integrations such as email, Slack, PageDuty or OpsGenie. It
helps you to manage alerts in a flexible manner with it's grouping, inhibition
and silencing features.

Fury Prometheus deployment (see [prometheus-operated](../prometheus-operated))
is already configured to automatically discover Alertmanager instances deployed
with this package.


## Image repository and tag

* Alertmanager image: `quay.io/prometheus/alertmanager:v0.16.0`
* Alertmanager repository: https://github.com/prometheus/alertmanager
* Alertmanager documentation: https://prometheus.io/docs/alerting/alertmanager


## Requirements

- Kubernetes >= `1.10.0`
- Kustomize  = `v1.0.10`
- [prometheus-operator](../prometheus-operator)


## Configuration

Fury distribution Alertmanager is deployed with following configuration:
- Replica number: `3`
- Listens on port `9093`
- Alertmanager metrics are scraped by Prometheus every `30s`


## Deployment

Before deploying this, please take a look at how to configure alertmanager [the
right way](../../examples/alertmanger-configuration).

You can deploy Alertmanager by running following command in the root of the
project:

```shell
$ kustomize build | kubectl apply -f -
```


### Accessing Alertmanager UI

You can access to Alertmanager dashboard by port-forwarding on port 9093:

```shell
$ kubectl port-forward svc/alertmanager-main 9093:9093 --namespace monitoring
```

Now you can go to http://127.0.0.1:9093 on your browser to see and manage your
alerts.

To learn how to add external URL to acess Alertmanager please see the
[example](../../examples/prometheus-alertmanager-externalUrl).


## License

For license details please see [LICENSE](https://sighup.io/fury/license)
