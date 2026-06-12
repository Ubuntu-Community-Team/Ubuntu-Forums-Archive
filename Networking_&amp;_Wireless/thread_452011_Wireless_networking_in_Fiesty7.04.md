---
title: "Wireless networking in Fiesty7.04"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by mathenge on 2007-05-22
It's pretty clear to me now that getting wireless networking in some laptop models/chipsets will take a lot of effort. This is NOT an out-of-the box, install-and-run thing. I have an Acer Aspire 5040 and a Dell Latitude D620. The Acer has an Atheros AR5005G wireless card and the Dell has a Dell card which basically has a Broadcomm chipset. On the Acer (a 64-bit machine) the wireless card is not even identified on boot. The madwifi drivers are painful to figure out and there are a ton of errors with the latest ndiswrapper source. Compiling it has too many errors. (I'll post them later just in case someone has a solution).

The Dell is closer to working. The hardware is detected but the drivers won't load. I can't find drivers for it. I blacklisted madwifi and went for ndiswrapper and gotten to the point where the package has compiled. I have the XP drives from my XP install and I've been able to configure them to load. I'm scanning for access points but see nothing. My AP is about 6 inches from the laptop and broadcasting so loudly the neighbours are complaining.

Oh well, it's very close. Once I have a solution for this machine/chipset, I'll post them here and see if it helps anyone. But in the meantime, if anyone has any of these two machines, especially an Acer Aspire 5040, I'd be very, very interested in knowing if wireless is working.

Incidentally, things were working perfectly fine in 6.06. God knows why I decided to upgrade!

Thanks for any feedback.

---

### Post by whitetrash on 2007-05-23
I'm not sure about the Acer (sorry) but the issue with the Dell is exactly the same issue I had with my HP (broadcom chipset).

This is what worked for me - [http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom).

The guide is how to install the firmware (if its already being autodetected you probably don't need to install the driver).

I tried the ndiswrapper way as well - that didn't work.

The link I posted is 100 times easier\quicker and worked great for me.

---

### Post by conxorxa on 2007-05-25
> **mathenge said:**
> It's pretty clear to me now that getting wireless networking in 
Oh well, it's very close. Once I have a solution for this machine/chipset, I'll post them here and see if it helps anyone. But in the meantime, if anyone has any of these two machines, especially an Acer Aspire 5040, I'd be very, very interested in knowing if wireless is working.

Incidentally, things were working perfectly fine in 6.06. God knows why I decided to upgrade!

Thanks for any feedback.
I have an Acer Aspire 5050 with a built-in Ather
os AR5005G wireless card and mine isn't working either with the built-in madwifi drivers.  The hardware is detected though.  I also tried ndiswrapper.  I was able to compile the latest sources. It loads the xp driver (net5211.inf) but doesn't create the wifi0 interface when I load the ndiswrapper module.  I didn't blacklist the ath modules but I removed them loading the xp driver and the ndiswrapper module.  I'm a bit suspicious that the xp driver is for a 32-bit os and ubuntu is 64-bit for my processor.

---

### Post by conxorxa on 2007-05-25
P.S. My wireless was working in edgy.

---

### Post by conxorxa on 2007-05-26
I finally got my wireless card working (Atheros AR5005G on Acer Aspire 5050).  The trick was to stop using knetworkmanager and do the connection manually with iwconfig and wpa_supplicant.  I also installed the latest madwifi drivers (0.9.3.1) but I'm not sure if that's necessary.

Have you tried installing the acer_acpi driver?  I read [here]("http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5005G") that you need that to get the ar5005g working on the 5040 but that could be old news (it's not dated).

---

### Post by ugm6hr on 2007-05-26
I wonder whether the Atheros5005G issue is because you're using the 64-bit Ubuntu.  I have an Acer5051 with the same card, and Xubuntu7.04 (i386 version) detected it, and after installing Network Manager (which is default in full Ubuntu7.04), it just works (some WPA issues, but minor).

No need to install drivers, ndiswrapper, nothing...  Xubuntu even defaulted to activating the Restricted Driver Manager for me - well, it at least warned me it wouldn't work without it and suggested I click in a box to make it work.  Being one for following instructions, I did.  It was easy.

Seems like no one else had that experience with the chipset, judging by the various posts I've encountered here.

---

### Post by lavinog on 2007-05-26
> **mathenge said:**
> 
The Dell is closer to working. The hardware is detected but the drivers won't load. I can't find drivers for it. I blacklisted madwifi and went for ndiswrapper and gotten to the point where the package has compiled. I have the XP drives from my XP install and I've been able to configure them to load. I'm scanning for access points but see nothing. My AP is about 6 inches from the laptop and broadcasting so loudly the neighbours are complaining.

Oh well, it's very close. Once I have a solution for this machine/chipset, I'll post them here and see if it helps anyone. But in the meantime, if anyone has any of these two machines, especially an Acer Aspire 5040, I'd be very, very interested in knowing if wireless is working.

Incidentally, things were working perfectly fine in 6.06. God knows why I decided to upgrade!

Thanks for any feedback.

Can you post what your Dell broadcom card is being detected as.
no one can really help you unless you do. all they can do is tell you what works for different cards.

I have a bcm4318 Airforce one...blah blah rev 02
there is a rev 01 that alot of people have solutions for that don't work for the rev 02.
I have experienced issues between different versions of ndiswrapper that some fail to work properly while previous versions did.

I am pleased to say though i don't have to use ndiswrapper anymore because fiesty has a newer version of fwcutter that works with my card.
you may want to look into that.

---

