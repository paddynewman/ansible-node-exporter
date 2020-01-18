# ansible-node-exporter

Download and install the Prometheus node_exporter.

# Run the playbook

```
$ ansible-playbook playbooks/node-exporter.yaml

PLAY [Install the Prometheus node_exporter] ************************************

TASK [Download node_exporter-0.18.1.linux-amd64.tar.gz to /tmp] ****************
ok: [localhost -> localhost]

TASK [Extrat /tmp/node_exporter-0.18.1.linux-amd64.tar.gz to /opt] *************
ok: [localhost]

TASK [Symlink /opt/node_exporter to /opt/node_exporter-0.18.1.linux-amd64] *****
ok: [localhost]

TASK [Create /etc/sysconfig] ***************************************************
ok: [localhost]

TASK [Install /etc/sysconfig/node_exporter] ************************************
ok: [localhost]

TASK [Install /etc/systemd/system/node_exporter.service] ***********************
ok: [localhost]

PLAY RECAP *********************************************************************
localhost                  : ok=6    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

```

# Verify the node_exporter

```
$ systemctl status node_exporter.service
● node_exporter.service - Node Exporter
   Loaded: loaded (/etc/systemd/system/node_exporter.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2020-01-18 13:50:02 UTC; 46min ago
 Main PID: 5767 (node_exporter)
    Tasks: 9 (limit: 4702)
   CGroup: /system.slice/node_exporter.service
           └─5767 /opt/node_exporter/node_exporter

Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - sockstat" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - stat" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - textfile" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - time" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - timex" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - uname" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - vmstat" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - xfs" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg=" - zfs" source="node_exporter.go:104"
Jan 18 13:50:02 paddy node_exporter[5767]: time="2020-01-18T13:50:02Z" level=info msg="Listening on :9100" source="node_exporter.go:170"
```
