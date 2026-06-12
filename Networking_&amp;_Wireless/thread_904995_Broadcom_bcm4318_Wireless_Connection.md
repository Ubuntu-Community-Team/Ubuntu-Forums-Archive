---
title: "Broadcom bcm4318 Wireless Connection"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by caleb.gross on 2008-08-29
Alright- I understand that there are already many discussions about the Broadcom wireless card and how to fix it. However, I'm having a lot of difficulty finding a solution to my problem. I'm relatively new to the Ubuntu scene so trying to understand all of this is mind-boggling.

So the problem:

I'm running an HP Pavilion ze2000 with the Broadcom bcm4318 wireless card. I've tried a lot of the things I've seen that have been fixing the connection for other people, but I keep getting the same results- my wlan light is lit up, it *says* I'm connected to my network, but I can't access the internet. If someone can just take me from step one and lead me through this that'd be great. Btw right now I'm on a wired connection so I do have an internet connection.. I'm just lookin to lose the wires.

---

### Post by Crafty Kisses on 2008-08-29
Post the results of ```
lshw -C network
```

---

### Post by caleb.gross on 2008-08-29
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ea:c4:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.103 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:1c:e4:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+ASUS,02/11/2005, 3.100.64.0 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by caleb.gross on 2008-08-30
can anyone help me out?

---

