---
title: "Not finding networks"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by TheEclypse on 2007-06-07
I have Xbuntu 7.04 installed, and a SiteCom WL-121 wifi card.  The card has been detected fine, and is using the ACX driver, and shows up in the network-manager.  However, when I go to choose a network, it does not display any networks in the list, and manually setting the ESSID doesnt get it to connect either. Anybody know what I should do now?

I have two routers available, one with WEP and one with WPA - I would eventually like to get it using the WPA one, but I figure I should sort that once ive got it connecting to things.

---

### Post by TheEclypse on 2007-06-07
I have just noticed that when I attempt to connect to the WPA router, iwconfig tells me the MAC address of the access point (which I do not get with the WEP router) - if I get WPA to work will it then connect properly?

---

### Post by hillbilly on 2007-06-07
Have you configured your card ? Try > sudo ifup eth0 NOTE: instead of eth0 substitute your wireless interface.

---

