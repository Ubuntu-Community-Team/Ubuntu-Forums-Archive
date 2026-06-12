---
title: "Uninstall network drivers"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by dhanjel on 2005-05-03
Hi,

can anyone give me any hints or tips on how to completely remove the ath_hal network drivers from my system?

They did not work with my network card so I need to install ndiswrapper instead.

---

### Post by Hagen Kaiser on 2005-05-03
[QUOTE=dhanjel]Hi,

can anyone give me any hints or tips on how to completely remove the ath_hal network drivers from my system?

They did not work with my network card so I need to install ndiswrapper instead.[/QUOTE]
 I have the same problem
I installed the ndiswrapper-drivers that work with my card( WG511) very well, but if I startup
the computer, hardware detection installs automatically a driver that does not work.
My workaround is (works only for hotpluggable devs):
Wait until the bootup says ndiswrapper loaded or wait until ubuntu is completly up and THEN insert the card. 
Furthermore I had to change in the /etc/iftable where it said eth1 to wlan0.

Then worked for me.

---

### Post by dhanjel on 2005-05-03
[QUOTE=Hagen Kaiser]I have the same problem
I installed the ndiswrapper-drivers that work with my card( WG511) very well, but if I startup
the computer, hardware detection installs automatically a driver that does not work.
My workaround is (works only for hotpluggable devs):
Wait until the bootup says ndiswrapper loaded or wait until ubuntu is completly up and THEN insert the card. 
Furthermore I had to change in the /etc/iftable where it said eth1 to wlan0.

Then worked for me.[/QUOTE]

Yeah that's the solution that I'll have to use as well, but I don't know how to remove the drivers, apt-get uninstall ath_hal?

---

