---
title: "New to Linux, need help with wireless"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Hydrothrax on 2008-08-28
Hi, I'm new to Linux (recently installed it from a live CD a friend gave me) and need help installing my Atheros AR5007EG wireless card. I run a dual-boot between windows and Ubuntu 8.04 (I'm stuck with beta) and only the windows part has internet access. Could someone help me with this please? Thanks :3

-Hydro

---

### Post by Crafty Kisses on 2008-08-28
Post the results of:
```
lshw -C network 
```

---

### Post by Hydrothrax on 2008-08-28
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:35:96:8d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

