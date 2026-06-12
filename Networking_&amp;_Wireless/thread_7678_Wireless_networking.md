---
title: "Wireless networking"
date: 2004-12-09
forum: Networking &amp; Wireless
---

### Post by paul.hendrick on 2004-12-09
Hi,
I'm still trying to set up a wireless network, but i can't even set the desktop machine to be an access point.
The way I understand it, I'll have my desktop, wired to my router...so

[internet]<-->(router)(Desktop1)<---wireless--->Desktop2.

So how do I get desktop1 to send a signal? I've used the network-admin tool to add the wlan device, but it WILL NOT enable. and (even after restarting the network service), the output of iwconfig still shows this:
```
wlan0 IEEE 802.11g  ESSID:off/any Mode:Managed 
```
when my essid is set to local_wlan, and i WANT the mode to be ad-hoc.

This is getting stupid now! ndiswrapper -l shows 
```
bcmwl5  driver present, hardware present
```

any ideas?

---

