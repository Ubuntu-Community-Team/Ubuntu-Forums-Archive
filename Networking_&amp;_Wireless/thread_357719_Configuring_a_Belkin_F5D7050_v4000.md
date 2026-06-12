---
title: "Configuring a Belkin F5D7050 v4000"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by Cippy on 2007-02-10
It took a while, but I finally got the ZD1211 drivers for this card to install. It shows up when I use the iwconfig command.

I am now attempting to connect it to my home network, but I'm having problems. I entered in the ESSID in the Network Settings. I don't have an encryption, so I didn't bother with that field. I've tried using both a static IP and DHCP, with no luck.

According to iwconfig, the network is listed, but I am "Not-Associated". In the connection properties window, the signal strength is constantly fluctuating greatly, being 100% at one point, 0% the next and pretty much everything between. Under status, it says "Disconnected". There is no listed activity in the window (nothing sent or received).

Anyone have any idea what's going on and how I can get it to work? Any help is greatly appreciated.

---

### Post by trippinnik on 2007-02-10
did you try iwconfig wlan0 up at the command line?  that one usually does it for me.  you may also want to try dhclient.

---

