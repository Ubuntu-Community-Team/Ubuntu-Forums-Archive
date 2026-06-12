---
title: "Wireless Cards working now"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by jgcamp99 on 2007-03-08
Incredible, I finally got the Proxim ABG 8480-WD to work over last weekend, and on a lark I put the Netgear MA401RA Rev D in and it works tonight. No joy with a D-Link DWL-650+ (ACX TI chipset) though.

So the list that indicates the MA401RA Rev D doesn't work is erroneous, I'm posting with it now, downloaded 318 files/packages out of the repositories earlier tonight with it too.

The Proxim, configured as ath0 using madwifi drivers from the restricted modules/repositories. The Netgear is configured as eth1 and I believe it uses the standard orinoco_cs drivers that the installation binds. I have an eth0, with this iwconfig and presume it to be my 10/100.

I know I had to reset my DI-614+ router the other night and oddly these two cards started to work flawlessly after a couple of weeks of installing all kinds of wireless packages in the repositories. I wish I could relay the step by step sequence but I got desperate and started doing all kinds of things, even reinstalls of things I had done previously. The best I could get was the Proxim to connect to an unWEPed network that my neighbor so generously broadcasts. But that's too far down the building to take advantage of for free and really doing it without looking like a total jerk piggy backing it. Anyway, Bellsouth DSL Lite for me and Edgy uses both these cards with the 22 Mbps network @ 11 Mbps.

I have screenshots for anyone that wants to reverse engineer this and perhaps emulate the success. Just tell me what you want me to post and I'll do my best to get back to this thread in a timely manner.

---

### Post by jgcamp99 on 2007-03-08
BTW, both cards are DHCP assigned. The Netgear MA401-RA Rev. D asks for a keyring password to unlock and connect. I can store the WEP/passphrase, but it still asks for the keyring unlock password. I've enabled root to login and it behaves the same, even though the Keyring for the WEP/passphrase is there permanently.

The applet that the keyring is managing is the nm-applet and it's located at:

/usr/bin/nm-applet

The Proxim 8480-WD simply connects with no prompts for security after storing the WEP/passphrase.

---

