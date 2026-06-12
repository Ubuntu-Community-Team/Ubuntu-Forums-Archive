---
title: "Setting up Broadcom 4306 B/G WLAN with no LAN on laptop with Edgy"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by eljaco on 2007-01-10
Hi,

I've spent over 2 days trying to figure this out and it has done me no good.

I'll start with the problem: I am trying to set up my wireless card (Broadcom 4306/Truemobile 1300) on a clean install of Edgy. For some reason, my LAN isn't working on my laptop, but I do have internet on my desktop, so I could easily transfer file (so long as they can fit in my 512 USB pen.) I have tried the Ndiswrapper approach using these how-to's:
[http://ubuntuforums.org/showthread.php?t=119468&highlight=broadcom+no+internet](http://ubuntuforums.org/showthread.php?t=119468&highlight=broadcom+no+internet)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
[http://ubuntuforums.org/showthread.php?t=25683&highlight](http://ubuntuforums.org/showthread.php?t=25683&highlight)

It does work on Windows XP (I dual-boot) but thanks to Broadcom, not on Edgy

Here are the computer specs: 
Dell Inspiron 8500
Broadcom 4306/Truemobile 1300 802.11b/g wireless card

EDIT: Also, it used to show my wireless card in the Networking application (from System > Administration) but after performing some things from the official Ndiswrapper page, it no longer appears, only showing the NIC and PPP cards.

If you need anything else, please let me know.

Thanks so much!

---

### Post by usererror on 2007-01-10
this may be a stupid question, but is your LAN port not working on the laptop because it is defective?? or is Ubuntu not detecting it?

---

### Post by eljaco on 2007-01-10
EDIT: The LAN issue I'm not too clear on. I think I'm going to call Dell and ask them to get me a new motherboard, but I just got it replaced about a month ago, so I doubt it's that.

---

### Post by eljaco on 2007-01-17
Done. Downloaded the .deb of ndisgtk and installed the ndiswrapper 1.8 that came in the Edgy CD and used the bcmwl5 driver from my windows partition (you can also get it from Ndiswrapper's Wiki.)

---

