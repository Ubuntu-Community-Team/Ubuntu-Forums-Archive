---
title: "could not find kernel image"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by rahtava on 2008-12-20
so i have live ubuntu on usb stick. It is booting on laptop but it won't boot on other computer because of that "could not find kernel image:"

So i enabled legacy support for usb under bios but it didn't help

any advice ?

---

### Post by cdtech on 2008-12-20
You have to make sure that the syslinux.cfg file is on your USB flash drive. Depending on which version of linux you have installed on your flash drive, the syslinux.cfg file could be at the root of the drive or within the /boot/syslinux or /syslinux directory.

If the file named isolinux.cfg exists and syslinux.cfg does not exists, rename isolinux.cfg to syslinux.cfg

If the syslinux.cfg file does exist and you still encounter the error, open the syslinux.cfg file with a text editor and make sure that the paths to your kernel and initrd files are correct.

---

### Post by rahtava on 2008-12-20
since I wrote that on one computer it works, it probably will not be a wine of non existing file and wrong paths ?

But of course i checked it before i wrote this post to the holy calm.

This file exist.

---

