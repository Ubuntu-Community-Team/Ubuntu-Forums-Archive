---
title: "Wireless cards show up, but won't connect to any networks."
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by MonoMatt304 on 2008-02-24
I installed xUbuntu on my old laptop (P3 700mhz, 256megs RAM, no integrated wireless) to see if I could maybe get some use out of it.  xUbuntu installed perfectly except for... surprise, any of my wireless cards I tried.

Here's what happens.

D-Link WUA-1340 - The system detects it and shows a bunch of networks in my area.  Unfortunately, when I try to connect to my WPA network, it repeatedly loops and asks for the WEP key, even though I put the right one it.

I tried using the driver wrapper thing (sorry, the name is escaping me at the moment) and I was able to connect to my network and browse the 'net... for about 30 seconds.  After that, the entire "networking function" on the system locks up (it will show my wireless strength stuck at like 70% even if I remove the dongle, and accessing "Networking" through "System" just doesn't work).

AmbiCom WL1100C-CF - After doing a search on here, it looked like this should work right out of the box with a PCMCIA adapter.  I stick it in my laptop and the thing lights up and all that.  xUbuntu is detecting that the wireless card is there (it showed up in "Networking"), but it will not detect any networks at all.  I tried using the driver wrapper thing here, too, but it doesn't even seem to matter since the wrapper tells me the hardware for that driver isn't even installed.

Any suggestions?  I would love to get wireless working on here.   I'm still kinda a Linux newbie, but I can find my way around and install stuff and run basic terminal commands.  Maybe I'm just missing something?

---

### Post by lswest on 2008-02-24
> D-Link WUA-1340 - The system detects it and shows a bunch of networks in my area. Unfortunately, when I try to connect to my **WPA** network, it repeatedly loops and asks for the **WEP **key, even though I put the right one it.

ummm, according to that you're trying to enter a WPA key into a WEP form?  that won't work, not sure if nm-applet supports WPA encryption (never use that) but i do know WICD does support it, try installing that then connecting to the network

*EDIT* you can download WICD off [https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=577210](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=577210) (choose the .deb file, it's easier to install)

---

### Post by MonoMatt304 on 2008-02-24
Argh, oops.  That should have been WEP for both.  The thing loops and keeps asking for the WEP key even though it's right.

And I've tried WICD already and it didn't work any better, unfortunately.

---

### Post by lswest on 2008-02-25
sorry about the delayed response, i was kind sleeping lol.   About the WEP encryption...sounds like you're going to need to install drivers for your cards, but since the second one is supposed to be functional "out of the box" you may be able to find a linux driver for it, at least, it seems likely.  I'm not 100% sure about it, but i'll have a look around once i get back from school.

---

### Post by lswest on 2008-02-26
i've been looking around and i saw this:
[http://www.dlink.com/products/support.asp?pid=477](http://www.dlink.com/products/support.asp?pid=477)
(first line is linux drivers, dunno if it would work for you), but you can take the XP drivers and use [this guide]("http://www.suseforums.net/index.php?showtopic=22109") to see if you can get the wireless working.  I know it's written for SUSE, but looks to me like it's universal.  Good luck.

---

