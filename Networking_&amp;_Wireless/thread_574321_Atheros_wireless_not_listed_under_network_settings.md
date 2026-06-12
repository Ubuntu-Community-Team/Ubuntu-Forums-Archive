---
title: "Atheros wireless not listed under network settings"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by Fir3chi3f on 2007-10-12
My issue is that the wireless isn't under network settings  (i want to use the madwifi drivers for those going to suggest ndiswrapper) although i dont see madwifi listed in lshw

Here is the specs:

```
 :~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:14:25:4d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.131 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

Ubuntu Gutsy 7.10 64bit
AMD Turion(tm) 64 X2 Mobile Technology TL-56 
1gb ram

If any other info is need please ask and all comments are appreciated.

---

### Post by Fir3chi3f on 2007-10-12
tryed  ndiswrapper, not sure what i did wrong

---

