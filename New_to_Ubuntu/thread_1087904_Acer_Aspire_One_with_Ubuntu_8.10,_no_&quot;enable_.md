---
title: "Acer Aspire One with Ubuntu 8.10, no &quot;enable wireless option&quot;"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by S0VERE1GN on 2009-03-05
I recently bought an Acer Aspire One netbook, little things great. I just deleted windows from it and im now trying to get ubuntu to allow me to activate wireless. YES ive flipped the wireless switch! doesn't seem to help! what am I missing? are there special drivers i need to worry about with this computer?

---

### Post by avtolle on 2009-03-05
From the command line (Applications>Accessories>Terminal) please do```
lspci
```and post the output. From other threads on your computer, I think it has the Atheros card, but we need to see before going any further.

---

### Post by S0VERE1GN on 2009-03-05
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Ather

---

### Post by avtolle on 2009-03-05
Thank you. Take a look at [https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan)

---

### Post by S0VERE1GN on 2009-03-05
pretty sure its the atheros as well, the drivers are in there as well when i check in admin options. just doesn't let me enable wireless...

---

### Post by anjilslaire on 2009-03-05
check this, it includes a script to build wireless driver for you:
[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

---

### Post by avtolle on 2009-03-05
I understand. Read the link and take the actions outlined; the "drivers are in there", but don't believe they work as initially presented without adding the backports module, etc. (which, BTW, works very well with my Atheros card on a Compaq F750US, which, according to Hardware Drivers, had the correct drivers activated, but didn't work until I installed the backports module). Good luck.

---

### Post by S0VERE1GN on 2009-03-05
you are undeniably the man! hopefully everyone else can find that link easily now as well.

---

### Post by S0VERE1GN on 2009-03-06
hmmmm...now i can't find any wireless connections...but i can enable wireless..it wokred for a while, een after a few restarts...now randomly doesnt work again...

---

### Post by anjilslaire on 2009-03-06
did you get a kernel update? Remember, you need to reinstall the madwifi after each kernel update. Luckily, we do't get those *too* often

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)
> 
The script will install the madwifi drivers into the kernel and also enable the wifi LEDs.  Remember though when Ubuntu updates ther kernel this module will have to be reinstalled.

---

