---
title: "Windows Vista Laod Issues"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by ozze121 on 2011-03-01
I am new to Linux and I think I made a critical error. I downloaded the USB installer and then downloaded Ubuntu 10.10, however, when I opened the installer and selected the Ubuntu .iso file I had it sent to my USB. I then ran my USB to start the install Ubuntu process and then had it Install to another USB device. Now Windows will not load unless the Ubuntu USB device is connected to my computer. The only way I can load my Windows is to select Windows Vista loader (/dev/sbd1) when the USB boots. If I do not have the USB in I get a black screen with grub recovery>

---

### Post by turtle153 on 2011-03-01
> Are you saying you just copied the .iso to your USB?

Sorry, I didn't understand. Have you tried installing Ubuntu again onto the hard disk?

---

### Post by Mark Phelps on 2011-03-01
That's because when you installed Ubuntu to your USB device, it installed GRUB to the "first" drive it found -- which is generally the internal drive.

Now, when GRUB boots, it must have your USB device connected or it will fail.

---

### Post by turtle153 on 2011-03-01
> **Mark Phelps said:**
> Now, when GRUB boots, it must have your USB device connected or it will fail.

If installing a new Ubuntu on the hard disk doesn't fix it, boot upUubuntu from the HDD and run```
sudo grub-update
``` in the terminal.

---

### Post by Rubi1200 on 2011-03-01
Although this link talks about an external drive, the principle is the same:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Follow the instructions there and you should be good to go.

---

### Post by ozze121 on 2011-03-01
> **turtle153 said:**
> Sorry, I didn't understand. Have you tried installing Ubuntu again onto the hard disk?
  No, I installed the .iso file via the USB intaller to a USB and then used that USB to install Ubuntu to another USB

---

### Post by ozze121 on 2011-03-01
Thank You this does sound like my issue and I will try it!!!!

---

