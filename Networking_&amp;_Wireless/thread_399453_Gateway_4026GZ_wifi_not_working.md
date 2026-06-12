---
title: "Gateway 4026GZ wifi not working"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by RHAnthony on 2007-04-02
I installed Ubuntu on my Gateway 4026GZ notebook but can't seem to get the wireless card to work at all.  I have put in SSID and keys, and even tried open networks as well.  I can get the ETH1 info to show up in ifconfig, and everything in the administrative tool window looks OK.  I can't however, seem to get it to take an IP via DHCP, or static IP put in through the window, or ifconfig.

Any thoughts?  Any similar problems?  Anyone else running on this laptop?

---

### Post by chili555 on 2007-04-02
How about letting us see ```
iwconfig
iwlist <wireless_interface> scan
```Your wireless interface may be eth1 or wlan0 or ra0 or otherwise. We'll get it.

---

