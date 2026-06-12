---
title: "what wireless network card / acesspoint?"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by dronepower on 2006-08-20
Im want to buy a wireless accesspoint and wireless network card for my PC.
which types / brands are known to run flawlessly on Ubuntu?

---

### Post by mjziegle on 2006-08-20
> **dronepower said:**
> Im want to buy a wireless accesspoint and wireless network card for my PC.
which types / brands are known to run flawlessly on Ubuntu?

Check out this site

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

Basically any card based on the following chips (I have the top 3) will work out of the box

atheros  AR52xx
zydas zd1211
ralink ra2x00
intersil prism (HostAP)

Please correct me if I am wrong, but typically

broadcom
TI
Marvel

are a pain and require wrappers.

IMHO atheros based cards are easy to find and offer a broad and robust driver that supports both Master and Monitor modes out of the box.  Prism cards do as well but are harder to find.  Zydas is in USB devices.

Any old access point will work without a problem.  Check out the reviews and find one that you like.

---

