---
title: "modem dial-up starting on start up"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2007-06-17
I have my modem working ok but it will start up every time I boot the computer.  It will start before I even get to the log in screen.  I have to disconnect the network conntion and go to gnome ppp and start the connection there.  Everything work fine from there. 

My question is how to I stop the modem from dialing out at start up. I have tried to disable the network connection and restart the computer but that did no good. 

Does anyone have any help on this.

---

### Post by ronbrooks on 2007-06-17
Problem has been fixed and this is how it was done for me any ways. 

I looked into this file with sudo nano /etc/network/interfaces and this is what I have now after I changed the last line to noauto ppp from auto ppp.

This is the output of of that file. 

auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ppp0 inet ppp
provider ppp0

noauto ppp0

I don't know if this will help you but now my modem will only dial out when I open the gnome ppp and hit connect.  I am now a happy camper.

---

