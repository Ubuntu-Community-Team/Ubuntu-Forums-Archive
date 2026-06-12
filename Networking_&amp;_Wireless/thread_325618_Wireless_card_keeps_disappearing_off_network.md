---
title: "Wireless card keeps disappearing off network"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Halfling Rogue on 2006-12-26
Hey, I just upgraded from 5.04 to Dapper. I'm still using the same wireless card that I was using before, a Truckstop brand Linksys WMP11 v4.11b. It was working fine on my old Ubuntu. But now, every time I shut my computer down and boot it up again, my internet connection is broken because my wireless card has somehow disappeared from my Network Settings Connection. Going into a terminal and running "sudo depmod -a" and then "sudo modprobe ndiswrapper" fixes it each time, but I'm tired of having to do this over and over. :-?

When I reinstalled my wireless card drivers on Dapper I followed the instructions on [http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) , including the part that said I should blacklist bcm43xx if running Dapper. I'm wondering now if blacklisting it is what maybe caused my problem.

Any help?

---

### Post by Floppyjoe on 2006-12-26
You need to add the word ndiswrapper to the end of this file /etc/modules.
```
sudo gedit /etc/modules
```
then save this file and exit.

---

### Post by Halfling Rogue on 2006-12-26
Awesome. Thank you!

---

