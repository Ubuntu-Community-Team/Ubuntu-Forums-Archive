---
title: "Belkin Wireless PCI Card - need help!"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by Golevel on 2008-10-25
```
lspci
```
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 Ethernet controller: Belkin Wireless PCI Card - F5D6001 (rev 20)

```
sudo ndiswrapper -l
```
net6001p : driver installed

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

....

Not sure what the issue it but there aren't any wireless options in my gui network area. Any ideas?

---

### Post by Golevel on 2008-10-25
```
lshw -C network
```

 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0c:6e:a1:d2:77
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.7.103 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Wireless PCI Card - F5D6001
       vendor: Belkin
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32

---

