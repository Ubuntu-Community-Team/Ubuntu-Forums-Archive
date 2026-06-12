---
title: "lshw -C network DISABLED"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Tombo5150 on 2008-05-08
I have been having problems on a friends computer enabling his wireless. Here is the output for lshw -C network:

```
 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:b2:94:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

I have been researching for hours and have tried several things but can't figure out why it is disabled. Thanks for any help.

Tom

---

### Post by amohanty on 2008-05-09
Can you post the output of 
sudo ifconfig -a
Is it disabled in the BIOS?
Is there a wireless killswitch on the laptop by any chance?

---

