---
title: "Wireless PCI card does not connect on startup and disconnects periodically"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by cemptor on 2008-05-07
I have a  Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) and an AMD64 installation of Ubuntu Hardy Heron

Used to connect fine with Fiesty Fawn (also 64 bit) - the wireless card would connect on boot, and be stable. I used a manual configuration and wpasupplicant.

My problems began with Gutsy and have gotten worse with Hardy.

First, my network does not connect on boot. Have tried using Network Manager and also manually editing /etc/network/interfaces

- I have to do a /etc/init.d/networking restart after boot
- With Gusty, the connection was pretty stable, but with Hardy it disconnects every few minutes, and I have to reboot my router. Restarting networking does not do it.

Please help me figure out how to fix this. 

The one thing that may be of note is that I upgraded from a fresh install of Fiesty to Gutsy and to Hardy. Also, I have Windows Vista on another partition and that connects fine and does nto disconnect periodically

Thanks!

---

