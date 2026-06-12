---
title: "VPNC Split-tunneling"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by freecode99 on 2008-03-16
HI all,

I have been using VPNC quite happily fro some time to connect to my Cisco VPN at work, but they recently changed the configuration to use split-tunneling and now I can't get any DNS resolution. I tried to update the PCF and import the current file, but get an error message that says "VPNC does not support split-tunneling over TCP.

Anyone have any ideas on how to make this work, or if there a way to get the actual Cisco Linux client for Ubuntu? All I have seen is a very old source file that is ancient code, and I am not sure that it will work in Gutsy.

advTHANKSance.

Chuck
](*,)

---

### Post by chilinski on 2008-03-16
Version 4.8x is available at the Cisco site. It's the current version for Linux.

---

### Post by gregmark on 2008-03-24
There is support for split-tunneling in vpnc 0.4.0, but you have to set some variables in a script.  Gunzip and read this:

/usr/share/doc/vpnc/README.gz

---

