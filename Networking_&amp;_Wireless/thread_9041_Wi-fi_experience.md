---
title: "Wi-fi experience"
date: 2004-12-23
forum: Networking &amp; Wireless
---

### Post by ubuntu1 on 2004-12-23
I thought I would share with you my experience of setting up my Sitecom WL-012 USB wi-fi adapter. After much experimentation I came up with the following. 

Obtain the wlan-ng package using Synaptic

Use a root terminal and type
[B]
modprobe prism2_usb prism2_doreset=1[/B]

then

**wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable**

then
[B]
wlanctl-ng wlan0 lnxreq_autojoin ssid=*yourssid* authtype=opensystem[/B]

then 

**dhclient wlan0**


I hope this helps.

---

