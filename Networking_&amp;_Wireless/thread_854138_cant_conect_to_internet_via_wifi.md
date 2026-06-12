---
title: "cant conect to internet via wifi"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by rahulerai on 2008-07-09
Hi all..I am new to ubuntu..I am using ubuntu 8.04.My problem is,i cant establish a connection to the router,though i configured my wireless card.I am using a static ip with no encryption,and i cant find a 'none' option among the password type..I fed up..Any one plzzzz help.....

---

### Post by rlzyoner on 2008-07-09
Well if you're sure that your router is not using WEP or WPA or some other form of security, then try connecting manually using the following commands

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID_IN_QUOTES"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

Where eth1 is the name of your wireless adaptor.

---

