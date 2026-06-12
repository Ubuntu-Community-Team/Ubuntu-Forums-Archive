---
title: "Wireless woes"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by matchstick on 2007-04-30
Ok just installed 7.04 desktop on a spare HD.  Its on the same comp with antoher HD running windows, and everything runs fine in win, so I know the hardware is good.  Im trying to get connected to my wireless network but i have had no such luck.  I have tried setting the name and key in roaming mode.  I have tried to set the network info in using manual mode.  Even tried to sudo the network.

Here's some info for you
00:0f.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
the adapter ID is eth2, and it seems to be working, just not picking up any networks, also scanning brings back nothing.

Any help would be greatly appreciated, and btw I haven't worked on linux in years so baby steps please.

---

### Post by AJL on 2007-04-30
I have the exact same card.  I got it up and running with ndiswrapper in no time at all.

Do a search for ndiswrapper bcm43xx.

It can be done!

---

### Post by Floppyjoe on 2007-04-30
You will need to either get your wireless card working with the native bcm43xx driver and use (fwcutter or firmware install from elsewhere) or you will need to get wireless working with ndiswrapper and the Windows drivers for your paticular card(which you can download from your computer manufacturers website).

---

### Post by AJL on 2007-04-30
wait!  I still had the post bookmarked..

**[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)**

---

