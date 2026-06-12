---
title: "Linksys WMP300N Wireless"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by Palerider07 on 2007-08-17
I've had a Linksys WMP300N since I first got my computer, for the sake of wirless connection. It works absolutely flawlessly on Windows XP, and never fails to work.

I have installed Ubuntu with some help, and it works as it should. Yet, when I check for the hardware that Ubuntu installed, it doesn't see the card or any wireless adapter. I could use some help connecting using it.

Help would be appreciated.

---

### Post by Palerider07 on 2007-08-17
Please Help!!!!!!!!!

---

### Post by Palerider07 on 2007-08-17
cant someone just hear me out?

---

### Post by Brightbelt on 2007-08-25
I have read as many posts as I can on the WMP300N and I've done searches many times. I still have not gotten mine configured, and not even with Ndiswrapper.  For some reason the INF file that currently comes with the WMP300N windows driver won't install with Ndiswrapper. It just does not fly for some reason.

Interestingly enough, I've seen a post or two where the person said that their WMP300N adapter "just worked", but it was never defined how.

So I don't think that's the norm on this one yet. I'm hoping a breakthrough will come on this adapter in time. 

Good Luck,...we'll need it maybe,

Frank B.

---

### Post by jml on 2007-08-25
At least part of your problem is the fact that this is very new hardware.  It supports the unratified 802.11n wireless networking standard.  So it is not surprising that ndiswrapper does not yet work with it.  As time goes on, support for this hardware will eventually be coded, but it may take a bit of time.  You may want to obtain an older, supported card on ebay and use it until your card is supported.

Joe

---

### Post by imperialline on 2007-08-25
> **jml said:**
> At least part of your problem is the fact that this is very new hardware.  It supports the unratified 802.11n wireless networking standard.  So it is not surprising that ndiswrapper does not yet work with it.  As time goes on, support for this hardware will eventually be coded, but it may take a bit of time.  You may want to obtain an older, supported card on ebay and use it until your card is supported.

Joe

It actually works and works pretty well. I have just installed a brand new LinkSys WMP300N on my machine. Here are the details of my machine:

1) dual AMD64
2) 2.6.20-15-generic (Ubuntu 7.04 64 bit)
3) ndiswrapper -v
   utils version: '1.9', utils version needed by module: '1.9'
   module details:
  filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
  version:        1.47
  vermagic:       2.6.20-15-generic SMP mod_unload 
4) ndiswrapper -l
    bcmwl5 : driver installed
     device (14E4:4329) present

All you need is to follow the instrructions from "bcm4306 ndiswrapper installation guide" ([http://ubuntuforums.org/showthread.php?t=340689&highlight=wmp300n](http://ubuntuforums.org/showthread.php?t=340689&highlight=wmp300n)) carefully.
Good luck

---

### Post by Palerider07 on 2007-09-01
Well, I can't seem to download ndiswrapper, considering im not connected. When I try to install it from the live cd, i get an error.

---

### Post by Palerider07 on 2007-09-01
Well, I can't seem to download ndiswrapper, considering im not connected. When I try to install it from the live cd, i get an error.

---

### Post by Palerider07 on 2007-09-02
bump

---

### Post by Palerider07 on 2007-09-04
Nevermind anymore. Thanks to this thread: [http://ubuntuforums.org/showthread.php?p=3284373](http://ubuntuforums.org/showthread.php?p=3284373)

Ihave no more troubles. Many thanks, aNewguy.

Sergey

---

