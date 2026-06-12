---
title: "Atmel USB wireless..."
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by jazzed on 2005-07-07
Quick background: I am a Gentoo user, and I have somewhat of an idea of what I'm doing in Linux; I'm not a new user or anything. I just installed Ubuntu for someone. The computer is a relatively old PIII. 


To the issue, everything went smoothly except the installation did not recognize the USB NetworkEverywhere NWU11B (which is simply a branded Linksys WUSB11). USB works otherwise; the mouse works and this USB adapter's power LED is on. The results of lsusb show me the word "Linksys", so it's somewhat recognized at least. 

I was a bit surprised, since the last time I installed Ubuntu on a laptop, the installation picked up what is probably the least Linux-supported wireless chipset of all, the Texas Instruments ACX100. Either way, this should be fine and all, since the kernel has a basic Atmel driver, right? Apparently not. Modprobing atmel appears to work, but iwconfig does not see the adapter. 

I tried the sourceforge driver, and the berlios (specifically USB) one. Neither of them would compile. They all left an error early on. I tried to get the kernel-headers off the CD (no internet connection without wireless), but that didn't help. It appears I can't compile anything. Coming from a source-based distribution, that's ridiculous. How could it not appear to compile anything out of the box? Or is it just a coincidence or something used by both these drivers that isn't working?

I even tried ndiswrapper, which works flawlessly with almost any Broadcomm chip it seems. In fact, I'm posting from a computer that's connected with the ndiswrapper module right now. The point is, I didn't expect this to work, but Ndiswrapper actually loaded the inffiles and claims that the hardware is present. Nidswrapper loaded, but I still can't use the usb adapter, so it didn't completely work. 

I have to work with the CD or downloads transferred via CD-RW here, since there's no internet connection. I'm not sure how to approach this now. I feel I could get this easily done if I could compile the third party drivers, but they all fail within a few lines (. Am I missing something obvious here? Thanks in advance.

---

