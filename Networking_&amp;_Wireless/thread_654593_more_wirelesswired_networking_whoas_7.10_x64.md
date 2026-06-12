---
title: "more wireless/wired networking whoas 7.10 x64"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by svtfmook on 2007-12-31
ok, i have been trying to setup an ad-hoc type network so that i can connect some portable wifi devices to my wifi card, then use my desktop's broadband internet connection .

my setup is as:
eth0 - internet
eth1 - wired network (bridged to eth0 so my media pc can access internet through my desktop, my desktop has dual lan btw)
wlan0 - wifi card on desktop, marvell 88w8335 card w/ driver netmw126 (i think that's what it was)


so, what i'm trying to set up is:

wifi device --> wifi card (wlan0) --> eth0 (wired internet)

now, as it currently stands, my internet works.  my wifi card is installed, driver works, detected, etc.  i can view wifi networks through my wifi card.  i've tried to setup ad-hoc in kwifimanager, wifi-radar and manually in terminal.  it will reflect that it's in ad-hoc mode in iwconfig.

firestarter will not start, it will tell my that eth0 is not connected, or, it will tell my that wlan0 is not connected.  so  i cannot enable internet sharing in firestarter.  although, i've always had problems with firestarter, it always failed on boot anyhow.

anyone have any idea?  i can't really find a good guide on ad-hoc or inernet sharing.  i followed this guide to setup wlan0
[https://help.ubuntu.com/community/Wi...cs%2FDevice%29](https://help.ubuntu.com/community/Wi...cs%2FDevice%29)

when i have wlan0 running, my wifi devices will see the network, but they cannot join the network.

i was able to have this working in windows btw.  so i know it's not a problem with the devices/card.

and i'm running the windowsx64 driver for the card.

so i gues i need to know how to get firestarter working properly and bridge wlan0 to my eth0.

---

### Post by svtfmook on 2008-01-01
anyone?


...bump

---

### Post by svtfmook on 2008-01-03
one last bump for help

---

