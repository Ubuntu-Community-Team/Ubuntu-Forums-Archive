---
title: "LinkSys WPC54GS Won't work -- help!"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by iainmcc on 2006-12-28
Cardbus card, Broadcomm BM4318 chipset.

Ubuntu 6.06 LTS, up to date, Toshiba Sattelite Pro M10 laptop.

Appears as 'eth2',  but there's no signal, and iwconfig says it has no wireless extensions.

Tried ndiswrapper, but that doesn't work either. Hunting through dmesg after booting with the card in place shows that pcmcia loads the bm43xx driver. There's no wlan0 anywhere.

Nice, but not useful. My router is running on channel 6. This can't be changed, as I have Windows boxes that only receive on ch6.

How do I get this card to work?

---

### Post by iainmcc on 2006-12-29
Never mind, all -- I have it all working at home, now.

First, I had to blacklist bcm43xx, then ndiswrapper was able to drive the device properly using the Windows driver from the accompanying CD.

I also had to set my router to channel 1 (2.412 GHz), even though the card appears to take iwconfig channel commands, it won't work on any other channel... 

Finally, much fiddling about with the Gnome networking sys tool before the device would even acknowledge there was a signal.

Now I just have to see if it'll work at my local Starbucks hotspot...

---

### Post by Silentvoice on 2006-12-29
Yeah, I had the same problem on my server machine (which runs gentoo, but still applicable) Same device, and for some reason the kernel's native support for the broadcom was built in (although I don't remember building it in, probably did when I got lazy and randomly started Xing in modules) But upon loading wireless tools, the oddest thing happened I had a wireless signal, which I was completely not expecting... just it had the functionality of a retarded child (broadcom chipset based doesn't necessarily mean the module will work)

My fix was I just rebuilt the kernel and took out the broadcom module, loaded ndiswrapper, and all was good.

---

### Post by Pobega on 2006-12-30
> **iainmcc said:**
> Never mind, all -- I have it all working at home, now.

First, I had to blacklist bcm43xx, then ndiswrapper was able to drive the device properly using the Windows driver from the accompanying CD.

I also had to set my router to channel 1 (2.412 GHz), even though the card appears to take iwconfig channel commands, it won't work on any other channel... 

Finally, much fiddling about with the Gnome networking sys tool before the device would even acknowledge there was a signal.

Now I just have to see if it'll work at my local Starbucks hotspot...

How do you do that exactly? I'm trying to get this exact Wireless card working on my sister's laptop, but I can't figure it out.

---

### Post by D_invictus on 2007-12-24
I've got a Toshiba Sattelite, It came bundled with Windows Vista, and has an Atheros wireless card built in. How do I get it to work on Ubuntu 7.10 Gutsy?

---

