---
title: "eth0 not present, network unclaimed"
date: 2015-04-05
forum: Networking &amp; Wireless
---

### Post by michal16 on 2015-04-05
Dear Ubuntu Users,

I am running Ubuntu 14.04 on my Samsung rf511 laptop.
Normally I use wireless network, but from time to time I have to use wired network which suddenly stopped working. When I plug in the wire, there is no effect - network manager doesn't report anything, ping doesn't work (connect: Network is unreachable). I am positive that both the cable and the network are working right now properly by checking it on another laptop with Ubuntu.

The result of the diagnose script is in the attachment - [ATTACH]261108[/ATTACH]. What concerns me is that there is no eth0 interface listed in /etc/network/interfaces and it is not listed when I type ifconfig -a. eth0 is listed as UNCLAIMED when I run the following:

```
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:f6c00000-f6c03fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:b000(size=256) memory:e2c04000-e2c04fff memory:e2c00000-e2c03fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: b4:74:9f:d0:20:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-46-generic firmware=610.812 ip=192.168.43.74 link=yes multicast=yes wireless=IEEE 802.11bgn

```

I am very grateful for any help.

EDIT: I am completely clueless why, but after **a few** reboots it worked without any problem :/ eth0 is now listed in /etc/network/interfaces and looks normal in lshw. Sorry for troubles.

---

