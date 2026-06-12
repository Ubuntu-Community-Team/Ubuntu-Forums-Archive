---
title: "WPA-PSK with WG311T"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by cccc on 2006-09-04
hi

I've Dapper Drake installed and I'd like to configure WPA-PSK with the wlan card WG311T from Netgear.

my wlan card was identified automatically as ath0

howto find out which module (driver) will be loaded for this wlan card ? 

kind regards
cccc

---

### Post by cccc on 2006-09-07
I found out:```

sudo lshw -C network

```

---

### Post by BombDiggity on 2006-09-07
Did you get the WPA support working?  I have the same card you do, and right now I can only access the home network if I have it unprotected.  How did you go about getting your netgear to go into WPA support?  Thanks

---

### Post by cccc on 2006-09-07
> **BombDiggity said:**
> Did you get the WPA support working?  I have the same card you do, and right now I can only access the home network if I have it unprotected.  How did you go about getting your netgear to go into WPA support?  Thanks

yep 

and because you asked so nicely, I've written the completed HOWTO:

[http://ubuntuforums.org/showthread.php?p=1474424](http://ubuntuforums.org/showthread.php?p=1474424) 

greetings
cccc

---

### Post by SkyScrap on 2007-06-08
How's the support for that Card under Ubuntu Feisty? Does WPA work with the network manager?

---

### Post by conjur3r on 2007-06-08
> **SkyScrap said:**
> How's the support for that Card under Ubuntu Feisty? Does WPA work with the network manager?

If I'm not mistaken, the Netgear WG311T uses an Atheros chipset which is known to have superb support in Linux.  I have the WG511T (pcmcia version of the WG311T) and it worked great in Edgy.  So great that I recommended it to everyone who asked.

That said, my wireless has been broken ever since I upgraded to Feisty and it annoys the hell out of me.  Feisty has issues with the card not being able to connect when the SSID is hidden.  Once it's broadcasted, it works fine.  Plain and simple: bug in Feisty and I hope fix it.

---

