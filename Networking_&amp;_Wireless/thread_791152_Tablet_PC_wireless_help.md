---
title: "Tablet PC wireless help"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by bschultzjames on 2008-05-11
Hey all, 

I'm very new to this whole linux / ubuntu thing.  I installed Ubuntu Studio on my HP/Compaq TC 4200 Tablet PC along side windows [because I am a ProTools user at heart].  

My problem is this:  I cannot get my wireless to even turn ON [let alone connect] in Ubuntu.  My wireless works fine in Windows XP, but for some reason the wireless will not even turn on in Ubuntu.  

Do I need to install a driver?  I have no idea what the problem could be.  ANY help would be appreciated.  



.b

---

### Post by daengbo on 2008-05-12
Do you know the model of your wireless card? Some models/manufacturers don't work in Ubuntu out of the box because the firmware required isn't available. The good news is that there is an emulation layer for XP wireless drivers on Linux. The program is called ndiswrapper. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for help getting it set up.

---

### Post by bschultzjames on 2008-05-15
My card is an Intel(R) PRO/Wireless 2200BG.  Is this one that I would need the XP emulator for?

Thanks,
.b

---

