---
title: "Can't get 2200BG + WEP to work"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by jdrietz on 2007-07-23
I have a Thinkpad T42 with a 2200BG card.  I am using the NM applet.

I have no problems connecting to non-secure wireless networks.  When I connect, my wireless LED blinks, so I know the card is powered on.  Connection is good.

However, when I attempt to connect using WEP to my WEP enabled network, the LED does not light up, and a connection is never made.  NM fails over to a non-secure network (I have free wireless internet where I live) and the LED light comes on.   

If I try to enter in the info manually with iwconfig, it never shows the "key" field value, so I am wondering if the key I am entering is not being saved.

I have tried following the instructions in a previous post at [http://ubuntuforums.org/showthread.php?t=399101&highlight=wep&page=2](http://ubuntuforums.org/showthread.php?t=399101&highlight=wep&page=2) in which I comment out everything in the /etc/network/interfaces file except for the "lo" settings..  No luck.

Please help - I am switching off of Windows (a major crash yesterday was the final straw) and this is the only thing holding me back at this point :-)

Thanks!

---

