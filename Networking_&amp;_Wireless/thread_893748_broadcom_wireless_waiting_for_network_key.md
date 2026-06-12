---
title: "broadcom wireless: waiting for network key"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by sstvinc2 on 2008-08-18
Hi all.  I've tried getting my broadcom bcm4318 (compaq presario r4000) working a bunch of different ways, and on Hardy and Gutsy.  They all seem to work to the same effect: my card is recognized, and it can find the wireless network that I'm trying to connect to.  But no matter what, it always just hangs on "Waiting for network key".  I've set up the network to use no encryption and WPA (which I'd obviously prefer), and neither of those work either.

Here's the output from lshw -C network:

```

  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:25:80:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bc:74:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

Any thoughts?  And please don't just redirect me to one of the standard tutorials.  I've tried several of them, with and without ndiswrapper.

---

### Post by sstvinc2 on 2008-08-18
I guess I should mention a couple of other things.  First of all, I can connect to the network with this card if the network is unsecured.  Furthermore, I can connect to the network using another laptop running Gutsy even with security on (with a different broadcom card, bcm4311).  So, it's not the network that's the issue, and my bcm4318 appears to only fail when the network is secured.  You may now resume your veritable flood of responses.

---

