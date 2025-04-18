# prometheus-kafka-exporter

[kafka_exporter](https://github.com/danielqsj/kafka_exporter) is a Prometheus exporter for Kafka metrics.

## TL;DR;

```bash
$ helm repo add gkarthiks https://gkarthiks.github.io/helm-charts
$ helm install --name kafka-exporter gkarthiks/prometheus-kafka-exporter
```

## Introduction

This chart bootstraps a [kafka_exporter](https://github.com/danielqsj/kafka_exporter) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm repo add gkarthiks https://gkarthiks.github.io/helm-charts
$ helm install --name kafka-exporter gkarthiks/prometheus-kafka-exporter
```

The command deploys prometheus-kafka-exporter on the Kubernetes cluster in the default configuration.

## Uninstalling the Chart

To uninstall/delete the `kafka-exporter` deployment:

```bash
$ helm delete kafka-exporter
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters and their default values.

| Parameter                                        | Description                                              | Default                     |
| ------------------------------------------------ | -------------------------------------------------------- | --------------------------- |
| `replicaCount`                                   | desired number of prometheus-kafka-exporter pods         | `1`                         |
| `image.repository`                               | prometheus-kafka-exporter image repository               | `danielqsj/kafka-exporter`  |
| `image.tag`                                      | prometheus-kafka-exporter image tag                      | `latest`                    |
| `image.pullPolicy`                               | image pull policy                                        | `IfNotPresent`              |
| `resources`                                      | cpu/memory resource requests/limits                      | {}                          |
| `service.type`                                   | desired service type                                     | `ClusterIP`                 |
| `service.port`                                   | service external port                                    | `9308`                      |
| `service.annotations`                            | annotations for service                                  | {}                          |
| `kafkaServer`                                    | Kafka server addresses as an array with port number      |                             |
| `annotations`                                    | pod annotations for easier discovery                     | {}                          |
| `labels`                                         | pod labels for easier discovery                          | {}                          |
| `rbac.create`                                    | Specifies whether RBAC resources should be created.      | `true`                      |
| `rbac.pspEnabled`                                | Specifies whether a PodSecurityPolicy should be created. | `true`                      |
| `serviceAccount.create`                          | Specifies whether a service account should be created.   | `true`                      |
| `serviceAccount.name`                            | Name of the service account.                             | ``                          |
| `prometheus.serviceMonitor.enabled.`             | Whether you would like to enable a serviceMonitor        | `true`                      |
| `prometheus.serviceMonitor.namespace.`           | The namespace to create the serviceMonitor in            | `monitoring`                |
| `prometheus.serviceMonitor.interval`             | Interval at which metrics should be scraped              | `prometheus-kafka-exporter` |
| `prometheus.serviceMonitor.additionalLabels.app` | Additional labels to add to the ServiceMonitor           | `{}`                        |

For more information please refer to the [kafka_exporter](https://github.com/danielqsj/kafka_exporter) documentation.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm install --name kafka-exporter \
  --set "replicaCount=1" \
    gkarthiks/prometheus-kafka-exporter
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name kafka-exporter -f values.yaml gkarthiks/prometheus-kafka-exporter
```
