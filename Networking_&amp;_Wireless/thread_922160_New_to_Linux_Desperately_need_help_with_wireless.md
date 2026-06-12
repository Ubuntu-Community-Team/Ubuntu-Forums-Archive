---
title: "New to Linux Desperately need help with wireless"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by sooner71 on 2008-09-17
Hi I am new and having an extremely hard time getting my wireless working with an Acer aspire 3004WLMi running:
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

bch4318

If I could get some fool-proof instructions that would be great!  Thanks!

---

### Post by nixscripter on 2008-09-17
What is the wireless card in it? Post the output of this command:

```
lshw -C network
```

---

### Post by sooner71 on 2008-09-17
This is what comes up after I type the above comman..
  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:10:d0:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=192.168.1.103 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1800-18ff iomemory:e2005000-e2005fff irq:169
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       resources: iomemory:e2000000-e2001fff irq:4
**

Thanks~!

---

### Post by nixscripter on 2008-09-17
Looks like you have a Broadcomm AirForce card. There are instructions for setting that up here: [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

