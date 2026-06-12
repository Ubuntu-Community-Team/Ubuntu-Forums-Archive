---
title: "network DISABLED"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by anttheman101 on 2008-04-12
i type in  lshw -C network and this is what i get

WARNING:you should run this program as super-user
*-network DISABLED
 description: Wireless interface
 product: BCM94311MCG wlan mini-PCI
 vendor: Broadcom Corporation
 physical id: 0
 bus info: pci@0000:01:00.0
 logical name: eth1
 version: 02
 serial: 00:00:00:1a:73:d2
 width: 64 bits
 clock: 33MHz
 capabilties: bus_master cap_list ethernet physical wireless
 configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

*-network
 description: Ethernet interface
 product: RTL-8139/8139C/8139C+
 vendor: Realtek Semiconductor Co., Ltd.
 physical id: 1
 bus info: pci@0000:02:01.0
 logical name: eth0
 version: 10
 serial: 00:1b:38:97:17:32
 width: 32 bits
 clock: 33MHz
 capabilities: bus_master cap_list ehternet physical
 configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 

well i do not know what all that means but i do not know why my wireless is disbabled, i have tried looking through differnent posts and thread about wireless problems but none has helped so far, anyone with any suggestions or solutions wood be great

---

### Post by Iowan on 2008-04-12
From the **man** page:> NOTES
       lshw must be run as super user or it will only report partial  information.
Check** /etc/network/interfaces ** to verify an entry similar to:```
auto eth1
iface eth1 inet dhcp
``` - if it's not there, add one and restart networking.

---

