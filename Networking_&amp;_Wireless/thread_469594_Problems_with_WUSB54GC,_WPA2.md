---
title: "Problems with WUSB54GC, WPA2"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by lunarmelody on 2007-06-10
I have a wireless network set up with WPA2, and I'm trying to install the WUSB54GC wireless card.  I've tried following the tutorials here for setting up WPA2 and the WUSB54GC card, but no luck.  The problem seems to be that it can't find the access point.  My wireless network is hidden, but there are others near here that are detectable (so says my windows install).  My ubuntu install, most of the time, cannot detect any of the other networks (iwlist scan returns nothing).  On occasion (very rarely), it will manage to detect the other networks, but still will not allow me to connect.

I've noticed, through experimenting and restarting my network drivers several times using "sudo /etc/init.d/networking restart", I get the following at the end of my output:
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1a:70:2f:4d:2d
Sending on   LPF/wlan0/00:1a:70:2f:4d:2d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping
```

It shows that I can't connect to the access point, but what does the "wmaster0: unknown hardware address type 801" mean?  Anyone have any suggestions on what's wrong?  Thanks!

---

### Post by lunarmelody on 2007-06-10
Found the problem.  My router was set up to use AES on WPA, instead of TKIP, which is not what I was told.  Fixing that on the router, plus using the tutorial here: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) fixed everything.

---

