---
title: "what is the name of that wireless thing?"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by corytoneill on 2007-03-03
I am trying to remember what the name of the wireless tool is that lets you selct which wireless network you want to connect to

---

### Post by jpkotta on 2007-03-03
Network Manager?

The one that gets run from the admin menu (the basic, default one) is network-admin.
The commandline tool that always works is
```
iwlist scan eth1
```
The "eth1" part may change.  Run iwconfig to see what your wireless interface is called.

---

### Post by Buster95 on 2007-03-03
Hello,
Another dumb question regarding network manager and wireless connections.
iwconfig tells me that I have no wireless extensions on Eth0, but describes the wireless router as connected to wlan0.
Why is that?
The reason I ask is that I can ping successfully but can't get a web page.
Cheers

---

### Post by jpkotta on 2007-03-03
eth0 is probably your ethernet card.  wlan0 is probably your wireless card.  If you can ping something on the internet (e.g. google.com), you have a working internet connection, and your inability to view webpages is caused by something else, probably on your machine.  A good guess is DNS misconfiguration.  If you can ping your wireless router or something else on the LAN, then you have a working network connection and the router is probably misconfigured.

---

