---
title: "Wireless connects, but doesn't fetch IP via DHCP"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Tsen on 2007-06-26
Hey guys.  So I've got an old, cheap Trendnet TEW 423 PI wireless card.  I use ndiswrapper for the driver, but it works fine--except for one quirk.

The card works, connects to the internet fine (I'm connected through it right now), but it won't get the IP address from the router.  It's set to "roam" mode, and when I click on the wireless network icon and select the network to connect to, it switches to the signal strength bars and says its connected, but when I view connection information, the IP address is all 0s and I can't access the internet.  
By running
```
sudo dhclient wlan0
```
I can get the internet working, but for some reason it never does it automatically.  Even after I manually run the dhclient, connection information still shows an IP of 0.0.0.0, but I can access the internet fine.  
If I try setting networks to "manual configuration" and enter "Obtain IP automatically...DHCP", and select the network to automatically connect to, it won't connect at all.

What's going on here?

---

