---
title: "Two Wireless Connections?"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by RetepNamenots on 2007-03-25
Hi guys, I've got a USB SpeedTouch 121g Wireless thing, and I've sucessfully in Edgy. However, because I have to use ndiswrapper for it, and it just so happens that that method of connecting isn't fully supported, the drivers I'm using for it crash Ubuntu every so often, usually when there's large amounts of information coming to or from the computer.

So, I dug out an old Belkin FD57000 - because I know that when I got this working in linux last time, it worked perfectly.

There's no way that I can physically connect the computer to a wireless router, so when installing the Broadcom drivers etc from the internet, I have to be connected via the SpeedTouch wireless USB.

How would I go about doing it?

I've tried a number of ways, and here are some outputs:

> pete@PETESROOM:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@01:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:fe9fc000-fe9fdfff irq:11
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:c5:67:59
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:fe9fe000-fe9fffff irq:201
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:bf:25:5e:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.22 firmware=THOMSON,05/19/2005, 3.3.25.0 ip=192.168.1.69 link=yes multicast=yes wireless=IEEE 802.11g


The very bottom one is the SpeedTouch USB - it runs from the THOMSON drivers.

I really want to get this working guys - otherwise I can't really download anything or update my computer..

---

### Post by RetepNamenots on 2007-03-25
Dont worry, I've fixed it, I think.

(Well I've taken the USB out, and I'm still connected, so I hope so :))

---

