---
title: "Wireless LAN Problem"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by deathspell on 2007-06-25
Hello,

I'm having problem getting my wireless card to work. It is a Linksys PCI Card for Desktop. I followed the instructions given on the forum for Broadcom 4318 Cards but the light won't turn on. I'm not sure what to do anymore. Please help me! :[

Model # - **WMP54GS** - Wireless-G PCI Adapter with SpeedBooster

I typed:
```

lspci | grep Broadcom\ Corporation
```

and the result is:
```

01:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by kevdog on 2007-06-25
Need to install ndiswrapper.

---

### Post by deathspell on 2007-06-25
I've installed it already. Even then the lights don't turn on.

Under Network, "Roaming" is disabled.. I've entered the SSID, For Password Type I have only two options (WEP Hexadecimal, WEP ascii) and a password.. So since I'm not using encryption while I'm testing the connection, I've left the password field blank. Not sure if thats a problem. I've never used WEP before.. I found it a little confusing with the 4 keys and pass and all that in the router settings.. WPA2 was easier but I didn't find such an option here. Should I look for something else to connect to my wireless network? I'm downloading Wireless Assistant to see if it'll do any good.

---

### Post by kevdog on 2007-06-25
Lets just check your installation before we proceed further.

Can you list:
ndiswrapper -v
ndiswrapper -l

ifconfig
more /etc/network/interfaces

---

### Post by jml on 2007-06-25
It took me quite a while getting my Broadcom based card working in Linux.  The information in this link is a bit dated, but it did finally help me to get my card working.  Hope it will be of some help to you.

[http://forums.debian.net/viewtopic.php?t=7949](http://forums.debian.net/viewtopic.php?t=7949)


Joe

---

### Post by deathspell on 2007-06-25
Okay, I'm an idiot, I guess. It worked fine in Wireless LAN Manager. But the card's light is still not turned on though. Why is that? The light works fine in Windows.

Secondly, Wireless LAN Manager does not show the wireless icon in the taskbar. Is there something else I can use instead? Preferably one that supports WPA/WPA2

My Ubuntu is GNOME based.

---

