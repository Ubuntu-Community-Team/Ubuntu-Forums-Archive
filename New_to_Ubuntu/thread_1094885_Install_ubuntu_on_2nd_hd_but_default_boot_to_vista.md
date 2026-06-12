---
title: "Install ubuntu on 2nd hd but default boot to vista?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by fanfare on 2009-03-13
Have had enough of Vista and tried wubi but other home users not happy to change.  I have PC with 2 hd.  1st hd partitioned (C: & E:) with vista.
2nd hd (D:) is from old computer which has XP plus backups on it.  1.  Can I reformat 2hd, & install ubuntu on it?  2. Can pc be defaulted to vista (hd C:) but allow me to switch to ubuntu (hd2)?

---

### Post by martrn on 2009-03-13
Yes if you know the size etc of the hard disk you want to install ubuntu to of course you can install it to any hard drive that can be booted to using the BIOS.

You can install it using the alternative cd or even the live CD and you can get in from [http://www.ubuntu.com/]("http://www.ubuntu.com/").  The Windowze community documents are located at : [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot") and it is also worth noting that you can [Dual Boot Windows and Linux Using the Vista Boot Manager]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx").  If you want to Install ubuntu to a second hard drive and do not want to annoy any other windowze users put grub on the second hard drive and not the first one.

Oh remember to back-up your back-ups and don't delete any FAT32 or NTFS windowze partitons that have vista on them.  Make sure you get the correct hdd and partition.

---

### Post by circa82 on 2009-03-13
Alternatively, for a cleaner and less hassle way of going about it, you could just switch the boot order of both hard drives. So the Ubuntu hdd would be first and the Vista hdd would be second. Then install Ubuntu to that first hard drive, setup GRUB to the first hdd's MBR and set the default OS in /boot/grub/menu.lst to Vista.

The nice thing about that setup is that Vista will boot by default, but more importantly, the MBR on the Vista hard drive will not be modified. You can switch the boot order at anytime and it will be as if Ubuntu was never installed.

---

### Post by fanfare on 2009-03-13
Thanks guys, I'll take a deep breath and give it a go.  I'll let you know

---

### Post by humphreybc on 2009-03-13
If I was you i'd just use the Wubi installer.

---

