---
title: "Can't enable Broadcom WiFi Card, Have no internet accesss!!"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by hackerlife on 2008-08-03
I just loaded the new Ubuntu 8.04.1 onto my hp dv2000 laptop, and am havin a helluva time trying to get my wireless card to work. I'm pretty much a total linux noob, but have tried many a commands in terminal to get it to work, and none seem to have any efffect. 
The worst part is, half the fixes seem to need an internet connection, which seems ironic as thats exactly what I don't have (I'm on my friends mac).

Please help!!
I need meh internets!!
I can post any info on the comp if you need it.

Wifi Card: Broadcom BCM94311MCG wlan mini-PCI (rev-01)
(Oh yeah, and its an amd64, just to make things moar fun :))

---

### Post by ThaRabbit on 2008-08-03
> **hackerlife said:**
> I just loaded the new Ubuntu 8.04.1 onto my hp dv2000 laptop, and am havin a helluva time trying to get my wireless card to work. I'm pretty much a total linux noob, but have tried many a commands in terminal to get it to work, and none seem to have any efffect. 
The worst part is, half the fixes seem to need an internet connection, which seems ironic as thats exactly what I don't have (I'm on my friends mac).

Please help!!
I need meh internets!!
I can post any info on the comp if you need it.

Wifi Card: Broadcom BCM94311MCG wlan mini-PCI (rev-01)
(Oh yeah, and its an amd64, just to make things moar fun :))

This is your solution:
[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

You can simply download the ndiswrapper-1.53.tar.gz package on another computer and transfer it to your linux box using an usb stick :)

you'll have to use a 64 bit version of the broadcom driver though, download that and use that in stead of the suggested WLANBroadcom.rar package suggested in that guide (those are 32 bit drivers)

---

### Post by hackerlife on 2008-08-04
I already tried parts of this, and I know that it won't work with out an internet connection (or so it would seem). It might work if ndiswrapper is all I would need, and it seems like I would need to get on the internet to download the updates. I can't even seem to get on dial-up!! 

Maybe I'm just linux-ly challenged...

Thanks for the help tho!!

---

### Post by hackerlife on 2008-08-04
Of course I'm trying that anyway...

---

### Post by superm1 on 2008-08-07
With the 4311, you can consider giving this a shot: [http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom+4311](http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom+4311)

---

### Post by hackerlife on 2008-08-07
ooh, thanks, but my friend already fixed this for me.
hes a freakin genius...
he brought over a usb wifi reciever thing and a flash drive with all the drives needed to install the usb wifi reciever. then, using our newfound internet, loaded the needed broadcom drivers.
but thanks for all the help everyone!

---

