---
title: "[SOLVED] Do I have a broadcom I don't know about?"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by 4lc0h0l1c on 2008-08-08
Hello,
AFAIK my computer does not have onboard wireless.  The wlan0 interface is the one I installed myself.  eth0 is my wired.  However, running lshw -C network results:
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.52+Ralink,03/08/2006, 1.00.05. ip=xx.xx.xx.xx multicast=yes wireless=IEEE 802.11g

---

### Post by Ayuthia on 2008-08-08
It does appear that you have a Broadcom card, but I can also see that you are using the RaLink drivers which appears to be working also...

What does lspci -nn show?  I would think that it will show up there also if you do have one.

---

### Post by mrsteveman1 on 2008-08-08
I can't think of any reason a 4306 chip would show up if there wasn't one in the system.

---

### Post by 4lc0h0l1c on 2008-08-10
I am an idiot.  I installed a broadcom 4306 a while ago and forgot about it.

---

