---
title: "Help with Broadcom BCM4318"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by ragna on 2008-05-24
I am a newbie who has attempted to set up ubuntu on a home PC

I'd just recently installed a Linksys WMP54GS v1.1 wireless adaptor. I have installed ndiswrapper and used it to install the drivers from the linksys website - "WMP54GS.inf"

I'd Discovered that the network was disabled though it seems to be enable from the network manager

```
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 02
       serial: 00:16:b6:99:c4:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.0.189 latency=66 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

Attempts to scan the network when roaming was on turned up no results.

How do I enable the network interface so as to detect nearby wireless networks? It worked for a while the first time I installed it, but stopped working after a reboot.

---

### Post by Steve413z on 2008-05-24
I had a similar experience with a buffalo card, the card would show up, but not display any of the networks, or even turn the light on, 

[http://ubuntuforums.org/showthread.php?t=803986](http://ubuntuforums.org/showthread.php?t=803986)

maybe this will help

---

### Post by ragna on 2008-06-02
Sorry for the late reply, haven't been able to get to use the computer recently.

I've Tried everything on that page besides recompiling the kernel. So far, no luck. In addition, no light shows up for the adapter.

In addition, I am currently using ubuntu 7.10

---

