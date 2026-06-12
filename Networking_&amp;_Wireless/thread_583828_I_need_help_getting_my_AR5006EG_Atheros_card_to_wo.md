---
title: "I need help getting my AR5006EG Atheros card to work in Gutsy"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by missingno on 2007-10-20
I tried getting Madwifi, but when I followed the instructions, the make command failed. Can anyone either help me get Madwifi to work or find a working driver for ndiswrapper? Sitting right next to my router with an ethernet cable is kind of inconvenient.

---

### Post by missingno on 2007-10-20
*bumps topic to the first page*
I've been searching Google, and I just can't seem to get anything to work with ndiswrapper. The driver(s) install, and it recognizes the hardware, but I can't actually connect to the internet using a wireless connection under the network config. Anybody have a solution?

---

### Post by missingno on 2007-10-21
I've been trying a couple more drivers, still nothing works. Anyone?

---

### Post by dr_cerebro on 2007-10-21
If you installed version i386, follow this steps:

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

If you installed version x86_64, follow the steps in this thread:

[http://ubuntuforums.org/showthread.php?t=580672](http://ubuntuforums.org/showthread.php?t=580672) but I recommend to read the thread complete because it has several modifications.  If your computer is an Acer laptop of the latest models then you will have to install acer_acpi first, but in this thread explains step by step how.

I hope it helps.

---

### Post by Ruiz on 2007-10-22
missingno, I'm in the same boat. Can't get anything to work. I tried the AR5007EG solution just posted, but it didn't work for me.

---

### Post by dr_cerebro on 2007-10-22
> **Ruiz said:**
> missingno, I'm in the same boat. Can't get anything to work. I tried the AR5007EG solution just posted, but it didn't work for me.

Did you disabled the Restricted Drivers first?

---

### Post by Jimerson on 2007-10-23
> **dr_cerebro said:**
> Did you disabled the Restricted Drivers first?

How do you disable restricted drivers?

---

### Post by dr_cerebro on 2007-10-23
> **Jimerson said:**
> How do you disable restricted drivers?

System-->Administration-->Restricted drivers and deselect Atheros

---

### Post by DJKMan on 2008-03-31
I too am having trouble on my Toshiba Satellite P250D-S7436 laptop. Any help would be appreciated.

---

