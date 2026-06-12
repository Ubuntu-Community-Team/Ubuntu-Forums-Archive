---
title: "linksys pcmcia card connection problem"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by fishwebby on 2008-05-21
Hello

Having successfully installed Xubuntu 6.06 the other day, I would like to be able to connect to the internet. Alas it won't let me. According to "lspci" I have the following wifi card:

Linksys WMP54G (Ver 4.5)
BCM4318 [AirForce One 54g] 802.11g
Wireless LAN controller (rev 02)
Subsystem: Linksys: Unknown device 0048

It seems to have detected the card ok, because in the network configuration window it shows it as eth1, but deactivated. When I change the settings and click "activate" it says "Activating interface eth1" for a couple of minutes, then "The interface eth1 is active". It isn't though because if I exit network configuration (something which takes ages too) and go back in it's deactivated again.

I've tried removing security on the router, changing from WEP 64 to WEP 128, inserting hyphens in the key, typing "restricted " before the key (I read it somewhere), tried plain ASCII and hexadecimal keys... I can connect from Windows no problem, so it's not a problem with the connection itself.

I'm anxious to start using Xubuntu but without internet access I'm a bit stuck - I would be very grateful for any help anyone can offer!

Many thanks
Dave

---

