---
title: "Realtek RTL8191SEvA: Wifi drops when reaching reasonable dl-speed"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by ventrikolo on 2013-09-26
So the problem: I have a 100mbit cable connection down stream, at broadband tests i clock around 24mbit/sec, but thats not the main problem. The annoying thing is that its not even av stable connection. Downloads in Deluge (torrents) and normal ftp only reach around 600kb/sec with the problem that as soon as it reaches around 500-600kb/sec the connection drops down to zero only to make another climb to the pretty peak of 600kb/sec. Anyone having the same problem? Its easy to follow in the system monitor and deluge.

```
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:4b:d6:ee:4b:04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-53-generic-pae firmware=N/A ip=192.168.0.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:c000(size=256) memory:d1800000-d1803fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: bc:ae:c5:37:22:35
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:b000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff


```

---

### Post by Bucky Ball on 2013-09-26
*Thread moved to **Networking & Wireless**.*

---

