---
title: "Agere systerm et131x pcie ethernet controller"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by kboysz on 2011-04-29
I just installed Ubuntu 11.04 amd64 on my laptop and cannot get my express card ethernet working.  The card works in a windows system.   Ubuntu recognizes the card but cannot connect to a network, need help enabling and setting up the drivers.

---

### Post by cariboo on 2011-04-29
Could you open a terminal and type:

```
sudo lshw -C network > network.txt
```

the above command will create a text file called network.txt, which you can copy to your Windows partition, paste the output in your next post.

---

### Post by kboysz on 2011-04-30
Here is what I get and my Broadcom wireless card doesn't enable.

 *-network
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:18:b2:c0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=1.8-3 ip=172.16.1.105 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fc300000-fc31ffff memory:fc325000-fc325fff ioport:1840(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e03fff
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:36:63:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f7f00000-f7f01fff
  *-network
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth3
       version: 02
       serial: 00:13:3b:e3:08:02
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=et131x latency=0 multicast=yes
       resources: irq:19 memory:f4200000-f43fffff memory:f4000000-f401ffff

---

