---
title: "rt2500, no dhcp"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by wildcard58th on 2005-04-11
I have an rt2500 based Asus Wlan card. I have followed the instructions in the Wikiki for configuring and Ubuntu 5.04 recognises the card under iwconfig and the gnome applet.

When I do "ifup ra0" the DHCP request recieves no offers. It is searhcing on 255.255.255.255 while my w/router is setup on 255.255.255.0.

I have reset the router (belkin), turned off wep brodcast the SSID. Still when I try o connect there are no DHCP offers. I have tried changing to a static IP/gateway etc and still nothing.

I have read about the RadioState being set to 1 instead of 0 but this seems to be (thread wise) an ndswrapper problem. Is it applicable to the rt2500 card? If so where do I check/change it?

Any ideas?

---

