---
title: "Q - router to modem connection"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by palmgrower on 2013-09-08
I have a UBEE cable modem/wireless router provided by Brighthouse. I disconnected wireless service, intending to use my old g router and save $4 a month. The Brightouse modem/router has 4 LAN ports, and my g router has 1 WAN and 4 LAN. How do I connect my g router to the modem/router? Do I have to buy a new cable modem that has WAN port? Thanks.

By the way, my desktops are wired. My wireless need is only occasional.

---

### Post by kwiadnyana on 2013-09-11
If I understand your setup correctly, then you will just have to connect one of the LAN ports (of your "old g router") to your modem. However, you need to take care of the wireless settings on your old g router (turn off DHCP since your modem does it, make sure that it has an address in the correct subnet, etc). That's it.

I am assuming that your "old g router" is a short for "old wireless 802.11g router"

---

### Post by chili555 on 2013-09-11
>  then you will just have to connect one of the LAN ports (of your "old g router") to your modem.I actually believe the cable modem needs to connect to the **WAN** port on the 'old g router.' Then any of the computers in your home that connect with ethernet can connect to the LAN ports. I would turn off both wireless and DHCP in the cable modem. Then specify an IP address in the 'old g router' such as 192.168.1.1. Turn on wireless and secure it with WPA2-AES and a strong password.

If you have but one device attached to the cable modem; that is, the router, it needn't operate its DHCP server.

---

### Post by kwiadnyana on 2013-09-13
> **chili555 said:**
> I actually believe the cable modem needs to connect to the **WAN** port on the ....

I just want to add that my reasoning behind connecting on the LAN (not WAN) port is that we alreadhy have the modem as the designated router. I used to have a Netgear WGR614 that has a WAN port for a cable modem. However when I moved to another country, we had a DSL with a built-in router, so I used the configuration I described above.

This way, I only have 2 classes of network, one in the WAN side, the other on the LAN side.

Of course you can also connect through the WAN side, but I am thinking you will need to have 3 classes of networks. One is the WAN side (assigned by your provider), the next class will be the intermediary between your modem and the WAN port of your home router (say, something like 192.168.1.xxx -- subnet 1), and then your LAN itself (my favorite will be something like 192.168.0.xxx -- subnet 0). DHCP needs to be turned on, on the home router.

YMMV

---

