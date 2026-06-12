---
title: "two network cards one disabled for some reason,"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by n1ght28 on 2007-12-10
hey i have two network cards one wireless one a new wired one,  problem is i can't get my wired network card to detect any networks, have even tried removing the wireless card but no joy, this is the output from  lshw -C network   as you can see the Ethernet card is disabled, how do i enable it. it is detected in network manager and is in roaming mode any help would be appreciated 

   *-network:0 DISABLED    
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:18:46:01:40:24
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 driverversion=2.0c duplex=half latency=64 link=yes maxlatency=40 mingnt=20 module=sc92031 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: wmaster0
       version: 00
       serial: 00:1a:70:a3:65:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.34 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

---

### Post by n1ght28 on 2007-12-10
bump

---

