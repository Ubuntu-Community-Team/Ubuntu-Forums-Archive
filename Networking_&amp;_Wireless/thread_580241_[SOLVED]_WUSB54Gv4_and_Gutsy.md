---
title: "[SOLVED] WUSB54Gv4 and Gutsy"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by mitchlourens on 2007-10-18
Gutsy has shown an improvement in wireless drivers as I can see, the hardware is seen and can be used.  But for some reason, I cannot get access to my 128 bit Hex WEP encrypted network.  Is there any reasoning for this? Am I still going to have to compile ndiswrapper from source and then install the drivers from the CD?

I've never, ever had luck with Ndiswrapper.  I can't just download it like all the tutorials say, because i don't have an internet connection without wireless!  I always get errors, but I'm just wondering if there is some bug in Gutsy that won't let me access the network.  

I almost forgot that I have the RC from a few days ago, if that makes any difference.

---

### Post by rustybronco on 2007-10-18
Had the same version, my advise is to scrap it! when I used it in windows and ubuntu 7.04 it dropped connections at random, it now resides in a drawer (and don't think I tried for a year and a half to get it to work) 
I have both netgear and linksys wireless routers, 2 linksys pcmcia cards, dynex desktop and pcmcia cards and no problems with them, but that wusb54g v4... now I buy cards with atheros chipsets.
I can't help you with 128 bit I had only used it with 64 bit wep, drop the router to 64 bit (that and mac filtering) and give it a go,

[http://ubuntuforums.org/search.php?searchid=29071206](http://ubuntuforums.org/search.php?searchid=29071206)
ndiswrapper can be gotten through synaptic, or sudo apt-get install ndiswrapper-common, then on your install cd for the wusb54g v4 go into the the .v4 folder>and grab the ?.inf . or pm me if you can't find to driver easily on linsys web site, the disc is in the drawer also...

---

### Post by mitchlourens on 2007-10-18
okay.. I'll see what I can do, I'm not the network admin :(.  Maybe I can get ndiswrapper to work, i've got ndiswrapper-common installed, but not utils, and it doesn't seem to have it on the CD.

---

### Post by rustybronco on 2007-10-18
browse the cd.    /pool/main/n/ndis...  just saw it on the cd i downloaded.

And welcome to the neighborhood!

---

### Post by mitchlourens on 2007-10-22
I've solved this by using the Ndiswrapper on the Ubuntu CD.  I then used the drivers supplied with the device CD (rt2500usb.inf and related files) and restarted.  At first, 128 bit hex WEP wasn't working, but after another restart it started working.  I'm actually posting this from the working machine!  Thanks for all your help rustybronco, it was greatly appreciated and I couldn't have done it without you.

---

