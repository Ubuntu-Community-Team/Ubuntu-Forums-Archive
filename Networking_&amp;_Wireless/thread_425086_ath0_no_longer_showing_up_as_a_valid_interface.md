---
title: "ath0 no longer showing up as a valid interface"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by herot on 2007-04-27
i started having problems with my wireless connection a few days ago...i could pull an ip address and ping the router and DSL modem.  I could not get out on the internet.  i couldn't ping [www.apple.com](www.apple.com). it was failing to resolve names and such. I tried some things and generally messed around with ifconfig, iwconfig, and iwlist (to scan). NOW, My computer cannot seem to *see* the router any longer... iwlist ath0 scan doesn't find it.  and the network manager cant pick up the signal.. (all of this was previously working before i started tinkering). I also started getting some error messages saying device not valid or not found (regarding ath0). I tried turning off the computer and unplugging the wireless card from the PCI slot and then booting without it, and then re-installing the card and booting again.  I am still having trouble... if anyone knows of a way to reconfigure network (similar to reconfig xorg), please let me know. I havn't upgraded my distro or anything like that.

---

### Post by herot on 2007-04-27
does anyone have any ideas about this?

---

### Post by herot on 2007-04-27
any ideas?

---

### Post by rjfioravanti on 2007-05-28
I am having a similar problem

I was downloading updates then the fire alarm went off so i had to close my computer and leave... so it turned off in the middle of the updates

When I turned back on everything seems ok, it is clear the updates did not finish because it is buging me about them still... however it no longer can find my wireless device

Usually my network interface is ath0.. but everything I try indicates that ath0 no longer exists. Ex it doesnt show up in ifconfig -a

sudo ifup ath0  just deies because it says no such device 

etc

---

### Post by mlentink on 2007-05-29
I have the same problem as well, after the last update of the kernel yesterday. 
ath0 can not be found anymore.
Aside form the kernel change, ***nothing*** else was changed, so I would assume it must have something to do with that.
I have a Sweex WiFi card, Atheros chipset that was supported without any problem until yesterday

---

### Post by mlentink on 2007-05-29
Update:

The Kernel update did not also install the necessary linux-restricted-modules-2.60.16

After installing them, evrythiong is ok again

---

