---
title: "cannot get the wireless to work"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by mr best buy on 2014-02-02
```
description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:03:25:17:6f:0c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.78 latency=32 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:e0206000-e0207fff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:17 memory:e0208000-e0209fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:cb:b7:34
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
```



I  typed in sudo apt-get update
sudo apt get install-b43-installer
then it tell me it can  not find anything
this is ubunutu 11.40
when I go to a more recient edition and it said it cannot use my processor. a celeron
how do I get wireless on this machine?

---

### Post by chili555 on 2014-02-02
> I typed in sudo apt-get update
sudo apt get install-b43-installerHow about:```
sudo apt-get install *firmware*-b43-installer
```

---

### Post by PotatoHead007 on 2014-02-02
When you say you cannot get wireless to work, do you mean that you can not find any AP's in your Network manager, or you can find them, but not connect? Also, i think that Ubuntu 11.40 is no longer supported. If newer versions give you trouble, try Lubuntu maybe?

---

### Post by mr best buy on 2014-02-02
yes that was the code I have been using. I mistyped it

---

### Post by mr best buy on 2014-02-02
I cannot get any version over 11.40 to boot. it says that the processor does not have the needed process.  SO I am stuck.  I tried LuBnute and Eutubu (sorry for the spelling...

---

### Post by chili555 on 2014-02-02
Your device requires firmware. Here is my post that describes how to get and install it: [http://askubuntu.com/questions/235049/my-mac-mini-late-2012-will-not-show-any-wireless-networks-ubuntu-12-10](http://askubuntu.com/questions/235049/my-mac-mini-late-2012-will-not-show-any-wireless-networks-ubuntu-12-10)

---

### Post by mr best buy on 2014-02-02
Thank you very very much..you are correct it worked..

---

### Post by chili555 on 2014-02-02
Awesome! Please use thread tools to mark Solved.

---

### Post by mr best buy on 2014-02-02
Darn it, i do not see where ot click this post as solved

---

### Post by howefield on 2014-02-02
> **mr best buy said:**
> Darn it, i do not see where ot click this post as solved

Thread tools.. up near the top of the page.

---

### Post by chili555 on 2014-02-02
Please check here:  [ATTACH=CONFIG]250037[/ATTACH]

---

