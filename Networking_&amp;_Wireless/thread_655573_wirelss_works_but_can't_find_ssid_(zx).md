---
title: "wirelss works but can't find ssid (zx)"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by ash477 on 2008-01-01
I can't connect w/ the wireless - I know the netgear wireless usb adapter is good - and ocassionally  the WiFi Radar shows other networks.  That means its a recognized adapter, right?  Now all I have done is disabled ssid broadcasting, and its a regular G network w/o any WEP.  Yet it can't find the network, when I type in the ssid.  

I installed ubuntu 2 weeks ago and its pretty much useless if I have to connect directly to my router (as I am now).  I can't have this stay in the kitchen :)

I've ran commands like sudo dhclient eth0    but no success.

---

### Post by ash477 on 2008-01-01
guess what - doesn't work with my USB wireless (it shows the network there but can't connect to it) but it works with my dlink PCI card....  The pain in the *ss is that it recognizes the wireless usb device!  If it didn't recognize it, or produced an error... that would make sense.  But to recognize it and simply not be able to find the network is painful.

---

### Post by bigken on 2008-01-01
could the reason it cant find your network is the fact that you have dissabled ssid broadcasting ?

---

### Post by ModelM on 2008-01-01
Have you connected via wireless at all? The reason I ask is that the network manager keeps a "list" of wireless networks it has connected to & tries those first. Try turning on SSID broadcast & connecting once to establish those connection settings in the network manager, then try it again with SSID broadcast disabled.

---

