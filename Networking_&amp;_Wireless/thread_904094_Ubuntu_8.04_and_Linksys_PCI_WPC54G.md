---
title: "Ubuntu 8.04 and Linksys PCI WPC54G"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by zdek on 2008-08-28
I installed Ubuntu this evening and am having trouble getting online.  When I type in sudo lshw -C network, I get:
*-network
   description: 802.11b CardBus

*-network
   description: Network controller
   product: BCM4306 802.11b/g Wireless LAN COntroller

*-network DISABLED
   description: Wireless interface

I've left some of the msg out as I'm just typing it in, but was alarmed about the "DISABLED" - I think that I have in enabled in the network manager.

Could this be a driver issue?  I don't have any propietary drivers installed.

Thanks!!
Joe

---

### Post by zdek on 2008-08-28
if needed,  when I type "iwconfig" in the terminal I get:

lo          no wireless connection

wmaster0    no wireless connection

wlan-       IEEE 802.11g   ESSID:""

---

