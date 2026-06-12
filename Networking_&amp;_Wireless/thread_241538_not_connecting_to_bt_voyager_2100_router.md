---
title: "not connecting to bt voyager 2100 router"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by dak-AD on 2006-08-22
Hiya all :)

I'm having trouble connecting to my home network.

Some info:

OS: ubuntu 6.06

Card: Trust speedshare pro turbo wireless PCI adapter
(works fine in winXP)

router: BT Voyager 2100
(for the moment, broadcasting SSID and no encryption. also no ip filtering, DHCP enabled)

basically, my card is being detected as ath0, its recognising all of the routers in the area that are broadcasting their SSID, including mine, and can even connect to the internet through one of my neighbours routers.

But not my one :(

I cant think of what could be stopping a card that works and can connect to routers from connecting to one particular router, apart from WEP which i've temporarily turned off :confused: 

So yeah, any help would be greatly appreciated :)

My tech level: not too knowledgable, not too naiive, very new to linux.  I know where the terminal is, but that's about it.

---

### Post by dak-AD on 2006-08-22
Ah, no worries.

in case it's usefull to anyone else, how i fixed it was:

sudo iwconfig ath0 essid "network name goes here"
sudo iwconfig ath0 key [1] "password goes here"
sudo iwconfig ath0 key [1]

then opened the GUI network thingy and selected my network and re-entered the password... wouldn't work if i only tried one of those ways, i had to do both :confused: 

Then it wouldn't persist a reboot. on someone elses advice, i checked /etc/network/interfaces, and after i'd opened and closed it the settings persisted a reboot.

thanks to anyone who looked at this to see if they could help :)

---

