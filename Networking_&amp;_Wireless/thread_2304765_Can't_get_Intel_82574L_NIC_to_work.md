---
title: "Can't get Intel 82574L NIC to work"
date: 2015-11-29
forum: Networking &amp; Wireless
---

### Post by superandyjamieson on 2015-11-29
Hey guys,

Can't seem to get this work, no matter what I try the connection looks active but no traffic transmits, adding it to /etc/network/interfaces hasn't worked for me.

Do I need to remove eth0 completely to get eth1 to work?

I'm using a HP N54L with Ubuntu Server 14.04.

Please see the output below,

```
sudo lshw -C network 
```

```
  *-network                      description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 00
       serial: 68:05:ca:2f:a4:bc
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.8-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fe8e0000-fe8fffff memory:fe800000-fe87ffff ioport:e800(size=32) memory:fe8dc000-fe8dffff memory:fe880000-fe8bffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 38:ea:a7:a3:2a:32
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5723-v3.35 ip=192.168.2.35 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:55 memory:fe9f0000-fe9fffff

```

Any help would be greatly appreciated,

Cheers!

---

