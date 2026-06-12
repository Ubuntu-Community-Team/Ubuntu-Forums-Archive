---
title: "Lost Wireless"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by bmachia on 2009-11-11
Hi all,
I just upgraded to 9.10 and lost my wireless on the laptop.  The blue connect light just keeps flashing.  
(I'm using my desktop to type this).

ndiswrapper is showing my wn511b driver installed
sudo dhclient wlan0 never receives a DHCPDISCOVERY
iwconfig shows
wlan0     IEEE 802.11g    ESSIS:off/any

Could someone offer an idea where I should look next?

Bill

---

### Post by bmachia on 2009-11-11
bump

---

### Post by RedSingularity on 2009-11-11
Did you check in System>Admin>Hardware drivers?

If its not listed there and you have installed it in ndiswrapper are you sure the module is loading?

---

