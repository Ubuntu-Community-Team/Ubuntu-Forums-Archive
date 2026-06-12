---
title: "No internet without 1st booting M$ XP"
date: 2005-09-03
forum: Networking &amp; Wireless
---

### Post by raif on 2005-09-03
bit of a weird problem: I have to boot up my computer up into M$ XP whenever I turn on the computer before then restarting with kubuntu (KDE 3.4.2) if I want to be able to connect to the internet.

I am using a belkin pci wireless card (with a broadcom chipset) to connect to a wireless adsl router.  

every time i start up kubuntu I have to log in as root into the shell and "dhclient wlan0".  whether I have already booted up in xp or not i still get exactly the same message but if i haven't booted up in xp despite the dhcp being bound, the wireless connection being perfect etc i simply cannot connect to the internet or even my own router whichever program i use.

i tried to change the .conf file, changing "eth0" to "wlan0" but that did not change anything nor did deleting the .conf file (after backing up).

if anyone could help me so that i don't need to type dhclient each time and also don't need to log into xp after having turned the computer on, i'd be really grateful.

thanks

r

---

