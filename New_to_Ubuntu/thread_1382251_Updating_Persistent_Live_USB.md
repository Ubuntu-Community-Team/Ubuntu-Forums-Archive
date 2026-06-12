---
title: "Updating Persistent Live USB"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by stevedti on 2010-01-15
I have been able to successfully create a bootable persistent live USB Ubuntu 9.1 thumb drive without problems by using USB Installer for Ubuntu v 0.2. on a Windows 7 machine. However, after booting from that drive and updating the files, using the Update Manager, everything seems to download and update OK but when I reboot, as indicated I should after the updates are finished, I can't boot into Ubuntu. 

I thought it might be the size of the thumb drive and that the updates were using too much space but I've tried this using a SanDisk Titanium 4 GB USB thumb drive installing the casper-rw with the 1.7, 2.7 and 3.7 GB images. No luck.

I've since picked up an 8GB thumb drive and would like to know if it's possible to update the files on the live USB drive. If so, what am I doing wrong? Is this a file system formatting issue? Should I be doing this on a Ubuntu system, using the ext(x) file system and not on a Windows machine with the USB formatted with FAT32?

Any help appreciated.

---

### Post by C.S.Cameron on 2010-01-15
On a persistent thumbdrive made with usb-creator, unetbootin, etc you end up with a bootable disk image. This image is not easily modified.
If you want to be able to update or upgrade you should do a full install, that is:
Disable or unplug your internal hard drives.
Plug in your target fllash drive.
Boot your Live CD or Live USB.
Select Install Ubuntu at the second screen, (the one after language options).
This will take more space than a "persistent" install" but will be act just like a full install to hard drive.

---

