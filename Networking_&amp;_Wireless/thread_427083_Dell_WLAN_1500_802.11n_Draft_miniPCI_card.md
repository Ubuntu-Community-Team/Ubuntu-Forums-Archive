---
title: "Dell WLAN 1500 802.11n Draft miniPCI card"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by sno2787 on 2007-04-29
I can not connect wirelessly from my 802.11n draft card. I've looked at tutorials time and time again and finally decided to post about it.

If anyone has a way to connect your 802.11n draft wireless card please tell me because im so lost! I just want to get on the internet without this stupid cord in my computer!

---

### Post by sno2787 on 2007-04-29
problem solved!

i used this tutorial

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

but what i also noticed when running the iwlist encryption command in the terminal is the system seems to only take 40/104 bit keys

so if you are having problems try changing to an ASCII WEP key and make it 104 bits

that works for me!

---

### Post by sno2787 on 2007-04-29
Again i take it back.

What i discovered when running iwlist encryption is that it only likes 140 bit WEP keys.

So i chaned my WEP key to a longer 140 bit one and followed the tutorial at the link mentioned above and there we go! Internet access! wooot!

---

