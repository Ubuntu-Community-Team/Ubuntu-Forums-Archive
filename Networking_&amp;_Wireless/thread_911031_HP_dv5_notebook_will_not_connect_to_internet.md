---
title: "HP dv5 notebook will not connect to internet"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by ArcadianRaider on 2008-09-05
I've just installed 8.04 LTS on my dad's new HP Pavillion dv5 notebook, and it will not connect to the internet. eth0 appears to be activated, but when I try to navigate to a page, the connection is dead. The nm-applet icon shows the ethernet as being connected.

Please help.

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lshw -C network
```

---

### Post by ArcadianRaider on 2008-09-05
I do apologise if this messes anything about, but I've installed Xubuntu on the computer and it connects to the internet via the ethernet cable fine, but still no wireless.

leon@lk:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:8d:34:78
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.0.0.7 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

[Edit]: Also, the wireless card was working when the computer was running Vista. The power indicator light for the card is red, but there aren't any buttons to turn it on or anything. Very confusing.

---

