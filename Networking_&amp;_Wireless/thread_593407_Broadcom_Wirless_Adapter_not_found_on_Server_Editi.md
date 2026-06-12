---
title: "Broadcom Wirless Adapter not found on Server Edition"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by brooky on 2007-10-27
Hmmm....

I'm trying to get wireless enabled over command line.

sudo lshw -C network
```
*-network:0
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:40:63:ee:1a:54
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100b                  t-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4                  .2 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes por                  t=MII speed=100MB/s
       resources: ioport:c800-c8ff iomemory:fdffe000-fdffe0ff irq:10
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 14
       bus info: pci@00:14.0
       logical name: eth1
       version: 03
       serial: 00:11:f5:14:f7:7a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-server latency                  =32 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fdffc000-fdffdfff irq:11
```

As you can see the broadcom device is found on eth1...

I try to enable it with:
sudo ifconfig eth1 up

But it returns:
SIOCSIFFLAGS: No such file or directory 

Does anyone know what that means?

---

### Post by brooky on 2007-10-27
I tried this guide:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) 

But you need a GUI. :(

Can it be done via command line?

---

