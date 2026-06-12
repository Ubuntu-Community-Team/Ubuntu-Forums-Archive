---
title: "Sharing Internet Connection Ubuntu &gt; XP Wireless"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by antieco on 2007-08-15
People:
Im trying to share internet through my ubuntu to my brother's pc running WinXP.
Ive installed madwifi drivers, and config it in adhoc mode.
but dunno how to continue. Plz any help?
I tried running firestarter but its gives me an error on ath0, and if i create a new device with madwifi wlandev as ath1 (adhoc mode) its give me the same error.

Im receaving internet from cablemodem (eth0) should i bridge it to athX?
Any idea????????????

---

### Post by spd106 on 2007-08-15
These wiki pages will  be useful,
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
[https://help.ubuntu.com/community/Router/Madwifi](https://help.ubuntu.com/community/Router/Madwifi)

I think you can use firestarter, but you will have to make sure that the ath0 interface is up and running before it tries to load.

---

### Post by DARKGuy on 2007-08-15
Hey!

Good luck with your internet sharing - that's similar to what I'd wish to archieve with my wireless card but the internet is in eth0 and I want to use my wireless card connected in my desktop to provide internet for my laptop, in other words using the wireless to use my desktop's ethernet from my laptop, which is XP too.

Firestarter is needed, but how do I make the bridge? what are the settings I must put in /etc/network/interfaces? my card is working and can scan for networks, I can set it ESSID and password and I can see it in WinXP, but I don't know how to setup the sharing if I'm sharing the internet from eth0 through rausb0 (which will be the "bridge") and not directly from rausb0?.

Any ideas?

---

