---
title: "Linksys WUSB54GSC"
date: 2017-12-09
forum: Networking &amp; Wireless
---

### Post by cdunivan on 2017-12-09
I just installed 16.04 on an old Dell Dimension 4600 desktop (32-bit architecture).

There's no wired connection because the router is in the living room. So I'm trying to install an old Linksys WUSB54GSC USB wifi dongle which, old as it is, still works on my Win7 desktop.

Am I right in understanding that it's no longer necessary to install ndiswrapper, that its functionality is included in 16.04? If I'm wrong about that, how do I get the .deb file to install?

Either way, I have the XP driver package in a folder on a thumb drive and copied into the Downloads folder in Ubuntu. But using the Additional Drivers utility I haven't been able to get it to recognize either hardware or driver.

My laptop is dual-boot Win7/Ubuntu 16.04, and custom desktop is Win7, both connected via wifi. So I'm able to download files with either of those and copy over via thumb drive.

---

### Post by wildmanne39 on 2017-12-09
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by chili555 on 2017-12-10
With the device inserted, please open the terminal and run and post the result of:```
lsusb
```

---

### Post by jeremy31 on 2017-12-10
See the wireless script link in my signature and post results.

chili555, I have one of these antiques and it shows as
```
ID 13b1:0026 Linksys WUSB54GSC v1 802.11g Adapter [Broadcom 4320 USB]
```
It works in 16.04

---

### Post by chili555 on 2017-12-10
I hope that's what cdunivan has and not the tricky V.2.

---

### Post by cdunivan on 2017-12-11
chris@chris-Dimension-4600i:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1737:0075 Linksys WUSB54GSC v2 802.11g Adapter [Broadcom 4326U]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chris@chris-Dimension-4600i:~$

---

### Post by cdunivan on 2017-12-11
Ah, crap. Yeah, it's a v. 2.

---

### Post by cdunivan on 2017-12-11
And I can't run sudo apt update because, like I said, there's no hard line connection in this room. If there was, I wouldn't be trying to use a wireless adapter, and this thread wouldn't exist.

"So I locked my keys with the electronic key fob in my car, and the guy told me to just use the keyhole on the driver's door to unlock it and get them out."

---

### Post by chili555 on 2017-12-11
> Am I right in understanding that it's no longer necessary to install ndiswrapper, that its functionality is included in 16.04? No. The package files still need to be installed. Do you still have the install USB or DVD? They can be found there.

Please see this long and depressing thread at post #6: [https://ubuntuforums.org/showthread.php?t=2028632](https://ubuntuforums.org/showthread.php?t=2028632)

The greater message here is that there are many threads here and elsewhere about your exact device and, as far as I've been able to Google, none ever get the device to work. None. 

We sort of pride ourselves here about being able to make anything work but this is probably not possible. I suggest that you look for a fully supported device and save yourself and me some agony.

Jeremy and my colleagues may have other ideas.

---

### Post by cdunivan on 2017-12-12
Well, I do also have a newer Cisco USB wifi dongle on my main desktop, so I could switch them out if it'll get the Ubuntu box working. It's an AE2500.

And I do still have the thumb drive I installed it from, using YUMI from Pendrive Linux.

---

### Post by chili555 on 2017-12-12
Yikes! It's another ndiswrapper device. Please look around and see if you have another.

A sad post about this device: [https://ubuntuforums.org/showthread.php?t=2214200](https://ubuntuforums.org/showthread.php?t=2214200)

---

### Post by praseodym on 2017-12-12
For the Linksys try this driver:

[https://media-cdn.ubuntu-de.org/forum/attachments/24/50/1597392-WUSB54GSC_modifie.gz](https://media-cdn.ubuntu-de.org/forum/attachments/24/50/1597392-WUSB54GSC_modifie.gz)

---

