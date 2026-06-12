---
title: "Ok, I'm a knucklehead"
date: 2005-06-27
forum: Networking &amp; Wireless
---

### Post by vandal43 on 2005-06-27
Ok, just installed vanilla Ubuntu 5.04 on a Toshiba Satellite A65-S126 laptop which has an Atheros AR5004G integrated wi fi. The installer detected the card fine, labelled the interface as ath0, but I think I messed up the config because I couldn't get it to connect to my access point.  I decided to forgo the wireless at the moment and stick to wired to get the system up to date with the intention of getting the wireless up and running at later date. Unfortunately, now ubuntu doesn't seem to detect the device anymore. I put the ath0 stuff back into /etc/network/interfaces, but  neither ifconfig nor iwconfig seem to think it exists. It's not listed in the Networking GUI either. Any thoughts on how to get it back? I'm stumped.

---

### Post by rockmusic88 on 2005-06-27
I might be wrong but shouldn't it be labled as eth0?

---

### Post by Lunde on 2005-06-27
[QUOTE=rockmusic88]I might be wrong but shouldn't it be labled as eth0?[/QUOTE]

No ath0 is correct when using the wireless driver for this chip.

What do you meen with Vanilla, did you upgrade your kernel to 2.6.12?
What's the name of the wireless card? did it work before?

---

### Post by vandal43 on 2005-06-27
No vanilla meaning stock ubuntu, I changed the kernel to the 686 version, but it's still in the stable 2.6.10 branch. I never got the card to associate to my AP, but I couldn't get my eth0 port to work either until I commented out all the references to ath0 in interfaces. Then the reference to the device just disappeared, doesn't show up in the networking list in gnome. Thanks for the quick replies.

---

### Post by Lunde on 2005-06-27
You never got your card to work? is it possible that it's a acx100 or 111 card instead of the Athlon chipset. Ubuntu chose the wrong drivers for me at installation. What's the name of the card?

If you upgraded from 386 to 686 and you compiled your wlan driver, you have to reinstall the driver.

---

### Post by vandal43 on 2005-06-27
Where can I find the driver? It's an ar5211 chipset I believe. Ahh you're right about the kernel though, hadn't thought of that. Does Ubuntu use madwifi as the driver for these Atheros chipsets?

---

### Post by Lunde on 2005-06-27
Sorry, Atheros, not Athlon chipset, it's supported by MadWifi, I don't think that's what Ubuntu use, but I'm not sure. Other people had the same problem.

This might be some usefull information:
Atheros AR5212 Madwifi HowTo
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

---

### Post by soonindallas on 2005-06-27
Can you see any access points with a scan ? My Acer has a built in IW2200 that i can activate and deactivate with a button/led for which the button function is supported but not the led function.  If you have a similar button you might try toggling it...

---

### Post by az on 2005-06-27
What does lspci show?

---

