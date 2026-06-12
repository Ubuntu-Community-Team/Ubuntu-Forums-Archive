---
title: "bcm43xx can't conect to wlan, wep"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by don durito on 2006-12-10
Hi,

I have setup kubuntu 6.10 on my brothers computer. downloaded and installed the cafuego bcm43xx driver with the deb file. i am able to activate my wlan card. and i already scaned my next wlans, which means my card is working. then i tried to setup my essid and the wep key but i am unable to connect.

I need this card working realy bad because it is the only way to connect to the internet with this machine. and i can't turn of the wep key. so if you can help me please remind there is no internet on this machine.

thanks in advance
don

---

### Post by FrodoB on 2006-12-10
When entering the WEP key into /etc/network/interfaces the key should be preceeded by "s:" if it is an ASII key. Here are two identical keys in the  two formats:

ASCII:
:dXx/;+@~Lt~a


HEX:
3a6458782f3b2b407e4c747e61


In interfaces:

ASCII:
wireless-key s::dXx/;+@~Lt~a

HEX:
wireless-key 3a6458782f3b2b407e4c747e61

Note how confusing ASCII can be the key begins with ":" and you prepend it with "s:" so you end up with "s::dXx/;+@~Lt~a"

Where to make wep keys:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

---

### Post by spd106 on 2006-12-10
The firmware deb isn't guaranteed to work, so it might be worth going down the firmware cutter route if you're not making progress.
Use the windows driver from the cd provided or download them from the website.

Also consider using ndiswrapper.

---

