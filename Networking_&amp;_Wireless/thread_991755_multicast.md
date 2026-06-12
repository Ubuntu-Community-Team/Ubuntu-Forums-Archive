---
title: "multicast"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by luceerose on 2008-11-24
I'm tweaking my modem settings on a wired network and I've stumbled across an option to enable/disable "multicast" - I am unsure of this option.
Option is currently disabled.
What ramifications might enabling this have on my network.
Can somebody explain to me ?

EDIT: It says "IGMP Multicast"
if that helps...

---

### Post by luceerose on 2008-11-24
Shameless BUMP

---

### Post by luceerose on 2008-11-30
Output of  sudo lshw -C network
shows;
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:d0:52:77:67
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.*.* latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```
You'll notice down the bottom it says multicast=yes
Should I take notice of this & enable that setting on my modem ?

---

