---
title: "netplan keeps adding interfaces that are part of a bond as default route"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by richpowell on 2019-02-04
Hi,

I have netplan configured such that two of my interfaces are a 802.3ad bond. The issue I'm having is that after applying my netplan configuration it seems that netplan still insists on setting the interfaces that make up the bond as the default route above the actual bond interface itself. I don't want netplan to add any routes to those individual interfaces. Can anyone tell me why on earth it's doing this and how I can stop it from doing so?

Here are my netplan configuration files:

/etc/netplan/01-netcfg.yaml
```

network:
  version: 2
  renderer: networkd


  ethernets:
    enp1s0:
      optional: true
    enp2s0:
      optional: true
    enp3s0:
      optional: true
    enp4s0:
      optional: true

```

/etc/netplan/02-bridges.yaml:
```

network:
  version: 2
  renderer: networkd


  bridges:
    br0:
      interfaces: [enp2s0, enp4s0]
      addresses: [192.168.1.1/24]

```

/etc/netplan/03-bonds.yaml:
```

network:
  version: 2
  renderer: networkd


  bonds:
    bond0:
      interfaces: [enp1s0, enp3s0]
      dhcp4: yes
      dhcp6: yes
      parameters:
        mode: 802.3ad
        mii-monitor-interval: 100ms
        lacp-rate: fast

```

And here is the routing table after I run "sudo netplan apply" or even reboot the machine (I am running Docker so the docker interfaces also show up):
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         67.170.72.1     0.0.0.0         UG    202    0        0 enp1s0
0.0.0.0         67.170.72.1     0.0.0.0         UG    204    0        0 enp3s0
0.0.0.0         67.170.72.1     0.0.0.0         UG    207    0        0 bond0
67.170.72.0     0.0.0.0         255.255.252.0   U     202    0        0 enp1s0
67.170.72.0     0.0.0.0         255.255.252.0   U     204    0        0 enp3s0
67.170.72.0     0.0.0.0         255.255.252.0   U     207    0        0 bond0
169.254.0.0     0.0.0.0         255.255.0.0     U     208    0        0 docker0
169.254.0.0     0.0.0.0         255.255.0.0     U     210    0        0 vethd01d043
169.254.0.0     0.0.0.0         255.255.0.0     U     212    0        0 vetha67b8e5
169.254.0.0     0.0.0.0         255.255.0.0     U     214    0        0 veth7dd8d67
169.254.0.0     0.0.0.0         255.255.0.0     U     216    0        0 vethfecc79a
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0

```

Notice how enp1s0 and enp3s0 are right at the top of the routing table.

So I manually run:
```

richard@server:/etc/netplan$ sudo route del default enp1s0
richard@server:/etc/netplan$ sudo route del default enp3s0

```


And then things are fine and I can connect out to the internet via the bond. I'd appreciate any help I can get here - I've been pulling my hair out for hours with this one...

---

