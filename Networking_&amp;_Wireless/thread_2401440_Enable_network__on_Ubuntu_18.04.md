---
title: "Enable network  on Ubuntu 18.04"
date: 2018-09-18
forum: Networking &amp; Wireless
---

### Post by fc-phoenix on 2018-09-18
Hello,, Please how can I enable network on **ubuntu 18.04**
i ran this command ** sudo lshw -C network**

here is the output.

[sudo] password for fc: 
  *-network **DISABLED **       
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 02
       serial: 00:1f:16:ee:5d:62
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d3700000-d371ffff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wls1
       version: 01
       serial: 90:4c:e5:01:e5:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.15.0-34-generic firmware=N/A ip=192.168.1.150 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d2600000-d260ffff.

I would appreciate any help.

---

