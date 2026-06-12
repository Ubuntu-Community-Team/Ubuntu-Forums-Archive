---
title: "Linksys WPC54GS"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by Hendriks on 2006-10-30
Hi evrybody!

Well i got a bit off a problem installing my wireless card (linksys WPC54GS) on a Kubuntu system (Edgy 6.10)!

I installed ndiswrapper the correct way, downloaded and installed the latest source code from site and installed ndiswrapper utils v. 1.8!

Then i follow the steps and downloaded the windows driver.

ndiswrapper -l
Installed drivers:
lsbcmnds driver installed, hardware present

after that i did the modprobe ndiswrapper and the ndiswrapper -m

I can see my wireless card in the network connections but it's called eth1 instead of wlan0 ???? And when i scan for acces points i can't find any ....

Can somebody help me?

Thx a lot!

---

### Post by Hendriks on 2006-10-30
The weard thing is when i try to enable eth1 in the network manager is that it automaticly turns to disbaled again ??

Anybody know this problem?

---

### Post by Ice1532 on 2006-11-23
if your still having trouble with this all you have to do is edit the file /etc/modprobe.d/ndiswrapper 

change wlan0 to eth1

---

### Post by mlissner on 2007-02-08
I am pretty sure the above advice is off (sorry). If you haven't done that, I wouldn't recommend it. It *sounds* like your install of the ndiswrapper and driver business didn't work, and that the card is showing up in the network configuration thingie (because it's a wireless card, and Kubuntu knows that much), but you can't make it work because it still lacks drivers.

I recognize the symptoms because mine's doing the same thing...arg...

Unless I'm mistaken, eth1 is your ethernet port (wired).

---

