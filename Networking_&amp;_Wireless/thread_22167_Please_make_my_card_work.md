---
title: "Please make my card work"
date: 2005-03-26
forum: Networking &amp; Wireless
---

### Post by t-bird on 2005-03-26
I have a roper freelan usb wifi card (its an intersil prism2.5 chip) i cannot make it work!  :cry: 

With linux-vlan-ng i cannot: make all and make install, i have this kind of errors:

cp: cannot stat `p80211.ko': No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/carl/Desktop/Wlan/linux-wlan-ng-0.2.1-pre19/src/p80211'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/carl/Desktop/Wlan/linux-wlan-ng-0.2.1-pre19/src'
make: *** [install] Error 2

with the .dep pack its ok but it as no "make config" :(

i read the how- to, i edit the file wlancfg - (mysssid) and  i can assign an ip address to wlan0 after: 

1)modprobe prism2_usb
2)wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
3)wlanctl-ng wlan0 lnxreq_autojoin ssid=myssid authtype=opensystem 

I can ping my self
but i cannot ping the other client! :(
its an ad-hoc lan.


With driverloader and ndiswrapper doesnt work at all.

Can u please help me, its about a month that i surf the internet to find a solution to make this card work!
I have Ubuntu warty, kernel 2.6

---

### Post by Plank117 on 2005-03-28
Abracadabra, Hocus Pocus, CARD BE FIXED!!!!

---

