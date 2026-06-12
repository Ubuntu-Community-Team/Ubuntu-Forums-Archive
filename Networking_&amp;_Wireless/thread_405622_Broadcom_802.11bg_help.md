---
title: "Broadcom 802.11b/g help"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by Give_Peace_A_Chance on 2007-04-10
Well, I have been just pluging in my Laptop with an ether net cable but I want to rome around.
 So I thought I could do it my self but i need some help, i cant find a driver for Broadcom 802.11b/g  wireless lan.
I need help getting my Computer connected to the wirless router.

---

### Post by josephus on 2007-04-10
there is a couple of threads about getting broadcom wireless to work.  search for you card name.

```
lshw -class Network
```

Gives information about your wireless card and will be useful to give out some details about your card when you need more help.

---

### Post by Give_Peace_A_Chance on 2007-04-10
Okay, i got it showing up on network settings. I activate it it says its active i press ok and After about  two min. sitting there waiting for the window to close i just closed it myself and then it was unactive agin.
HELP!

 *-network:0 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:b6:ce:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0201fff irq:225
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:37:73:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too ip=192.168.0.102 multicast=yes
       resources: ioport:a000-a0ff iomemory:c0202000-c02020ff irq:217

---

### Post by josephus on 2007-04-10
what have you tried so far?

have you looked at:

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

my understanding is that broadcom wireless cards don't work straight out of the box.  even though there is a driver (bcm43xx) included in the basic install, these drivers don't include the necessary firmware to properly control your wifi.  The second link shows how a firmware cutter can be used to solve the problem.

The first link uses the ndiswrapper to get your card going.  Basically it takes a windows driver and wraps the interface to get it going in linux.  Give one of these methods a go.

---

