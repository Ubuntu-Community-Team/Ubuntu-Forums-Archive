---
title: "WMP54g (4.1) is not letting me use IPv4"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by theyain on 2007-09-12
I just got a WMP54g from Wal-Mart, and it seems that I can't use it.

I'm on 7.04.  Most of my computer is sadly VIA, so I have some problems here and there.  So this could be caused by that.

I when I click the little icon for my network connection, I can actually see the SSID of the WLAN and choose it.  It says I am connected, but when I use the Wi-Fi Radar from the Repoz, it says my IP is the loop back IP.  when I go into network tools, I don't see anything for IPv4 for ra0.  

I also entered " dmesg | grep ra0 " into my terminal and get this:

[16445.529720] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[16455.948464] ra0: no IPv6 routers present

Obviously I can't use the protocol IPv4.


Any help?  Sorry in advanced if I am confusing.  I can get like that.

---

### Post by theyain on 2007-09-13
Bump

---

