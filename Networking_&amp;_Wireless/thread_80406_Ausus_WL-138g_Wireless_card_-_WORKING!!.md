---
title: "Ausus WL-138g Wireless card - WORKING!!"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by aivars on 2005-10-22
At last!
It was necessary first to install ndiswrapper, then it is necesary to install Marvell Technolgy Windows drivers (for XP; i could not get windows 2000 drivers to work; i use windows 2000) and then - i got the feeling that first it was necessary to manually (with ifup/ifdown) get the card working - initially with autoloading from etc/network/interfaces the card did not pick up my network ESSID; i had to assign it manually with iwconfig.
Also, i disabled WEP encryption and got the card working first, then i put the following lines in my /etc/network/interfaces

iface wlan0 inet dhcp
wireless-essid MyESSID
wireless_keymode open
wireless_key myHEXkey (these are numbers)
wireless_mode managed
auto wlan0

Now finally it works. The only thing is when started automaticall the card takes very long time to start up. With ifup it is very quick. I do not know the reason why.

Thanks to everyone who responded to my cries for help!

Aivars

---

### Post by ForceAbuser on 2006-01-10
aivars,
it seems like a lot of work for a n00b like me...

could you recommend this card? or could you make a tutorial for the installation?

ForceAbuser

---

