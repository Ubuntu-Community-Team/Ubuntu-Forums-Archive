---
title: "Help with connecting to net"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by sALVO-7 on 2008-07-28
I just Ubuntu 8.04 and i cant get access to the net. Iv'e been looking around the forum to see if I could find a solution. I have found a few posts but i wanted to see what people would say with my details.


installed *-network:0             
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:11:95:1c:8a:59
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:12:17:94:ae:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by superprash2003 on 2008-07-28
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Kevbert on 2008-07-28
Please check out this [COLOR="Red"][post for BCM4306]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")[/COLOR].

---

