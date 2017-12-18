#  <p style="text-align:center">Cassandra dashboards & alerts for prometheus-boshrelease</p>
> > ** THIS RELEASE IS STILL UNDER CONSTRUCTION
----------

## Introduction
This release is used as an extension of prometheus deployment.
It adds missing [grafana dashboard](https://grafana.com/dashboards/371) and prometheus alerts.

## Usage
To deploy the grafana dashboard, edit your prometheus deployment file:

```
releases:
...
  - {name: cassandra_prometheus, version: latest }

instance_groups:
- name: prometheus-server
...
  jobs:
  ...
  - name: cassandra_alerts
    release: cassandra_prometheus
  - name: prometheus
    release: prometheus
    properties:
      prometheus:
        ...
        rule_files:
        ...
          - /var/vcap/jobs/cassandra_alerts/*.alerts


- name: grafana
...
  jobs:
  ...
  - name: cassandra_dashboards
    release: cassandra_prometheus
```
