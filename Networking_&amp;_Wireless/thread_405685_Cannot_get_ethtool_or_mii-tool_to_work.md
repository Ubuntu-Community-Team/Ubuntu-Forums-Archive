---
title: "Cannot get ethtool or mii-tool to work"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by langywhips on 2007-04-10
Hello

First post on the forum, been using Ubuntu for 6 months now and like it so much decided to make a file server using Ubuntu Server.

However, I would like to bond two Gigabit network cards and I can't get any information from the cards with ethtool or mii-tool.  

I tried just putting one card in and getting that one to run at 1000baseT/Full but I cant force it.  Every time I try ethtool, I get No data available.

I have tried using ndiswrapper with the XP driver and I still can't change the settings of the card.

The card I am trying to use if Asus NX1101 and I am running Ubuntu server 6.06.  Has anyone any ideas?

Thanks

---

### Post by handaxe on 2007-04-10
First off - not all cards support the functions used by either tool. Eg my Realtek 8168 gives nothing with mii-tool but does with ethtool.

However, you need sudo:

```
sudo ethtool ethx/ath0 etc
```Same for mii-tool.

HA

---

### Post by langywhips on 2007-04-10
Hi

I did use sudo for both ethtool and mii-tool but still got no results.  Does this mean I have to buy new cards?

---

### Post by handaxe on 2007-04-10
```
~$ sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Operation not supported
```Ethtool gives the "No data available" message, I believe. If the above is what you get with mii-tool then yes, I would think that the cards are lacking.

I am not sure what "bonding" means, (not to do with super-glue I am sure :)), so the implications are yours to know... (Ok, I know now - thanks google..)

Good luck,

HA

---

