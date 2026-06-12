---
title: "Wireless network not working. RT5592 PCIe"
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by william107 on 2016-05-03
Hey guys, i have looked around for a couple of days for a fix for my desktop. The wireless wont work.

sudo lshw -C network came out with:
```
  *-network UNCLAIMED       description: Network controller
       product: RT5592 PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 70:71:bc:ce:6f:16
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.134 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:feac0000-feafffff ioport:ec00(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: ham0
       serial: 7a:79:19:51:85:bb
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full ip=25.81.133.187 link=yes multicast=yes port=twisted pair speed=10Mbit/s



```

After trying to fix this issue, i ran the code again, now with the following results:

```

  *-network DISABLED
       description: Wireless interface
       product: RT5592 PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 70:71:bc:ce:6f:16
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.134 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:feac0000-feafffff ioport:ec00(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: ham0
       serial: 7a:79:19:51:85:bb
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full ip=25.81.133.187 link=yes multicast=yes port=twisted pair speed=10Mbit/s



```

Any help would be appreciated!

---

