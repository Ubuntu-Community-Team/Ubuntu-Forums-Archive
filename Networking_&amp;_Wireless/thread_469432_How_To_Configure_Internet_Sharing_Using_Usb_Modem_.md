---
title: "How To Configure Internet Sharing Using Usb Modem And  Switch"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by oliboli on 2007-06-09
HELLO!
need some help to share my internet connection with my other computers .
There is a switch between my computer and the others.
the connection between the modem and my pc is made by USB.
the connection between my pc and the switch is made by inboard network


Thanks in advance!

---

### Post by spd106 on 2007-06-12
Two links [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) and [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

The internal interface will probably be eth0 and the external will probably be ppp0. Basically your PC will function as a router, forwarding traffic to the LAN (via the switch).

You might want to consider installing firestarter to aid you with configuring the firewall/router seetings. It's available through Add/Remove programs or Synaptic.

---

