---
title: "Wired connection not working, Ubuntu 14.04 LTS"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by SurachaiRobotic on 2015-02-18
I can't access the internet.
Thank you.

```
hatori@hatori-X450CC:~$ sudo lshw -C network[sudo] password for hatori: 
  *-network               
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: bc:85:56:10:e3:9b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-32-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7910000-f791ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: eth0
       version: 0a
       serial: 74:d0:2b:be:7e:37
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.1.1 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:f7810000-f7810fff memory:f2100000-f2103fff
hatori@hatori-X450CC:~$ 

```
[IMG]https://imagizer.imageshack.us/v2/1366x768q90/631/oxjmqs.png[/IMG]

---

