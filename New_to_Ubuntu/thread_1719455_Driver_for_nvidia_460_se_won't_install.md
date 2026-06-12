---
title: "Driver for nvidia 460 se won't install"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by horselover phat on 2011-04-01
I'm a complete newb to ubuntu, checking out Meerkat via a persistent Live USB. Tried to install and activate the proprietary driver for the 460 SE, but got:

> SystemError: installArchives() failedAnd then:

> Sorry, the package 'nvidia-current260.19.06-0ubuntu1 failed to install or upgradeI submitted a report to Launchpad, which can be found [here.]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747895") It's mostly too technical for me to understand, but one thing that jumped out was

> glxinfo-Error:[Errno2] No such file or directoryAnything to do with it being a Live USB, not a full install?

Any help gratefully received. I really like ubuntu from the little I've seen from it so far, but need better resolution for it to be usable!

---

### Post by beew on 2011-04-01
I don't think live usb with persistence supports installation of propietary graphic drivers (Maybe things have changed in 11.04, but I don't believe it would work in 10.10)

---

### Post by horselover phat on 2011-04-01
I wondered if that might be the case. Would Wubi support the proprietary driver? I really want to make sure the basics work ok before I undertake a full install!

---

### Post by beew on 2011-04-01
I won't recommend Wubi, but you can do a full installation in an external hard drive, or even a USB flash drive (but that would be slow)

If you have a full install you can do anything you would as in an internal install.

To do that you need a live usb (or a live CD) for installating, another usb (or an external hard drive) to install into.

Boot into the live usb, choose install manually. Then choose the target drive (make sure you choose correctly or it will wipe out your internal drive) The target should be something like sdb or sdc. (sda would be your internal hard drive) You need to format the target in ext4. If you are using an external harddrive you may want to create two ext4 partitions, one as / and the other as /home (for data and settings). After that make sure you install the bootloader in the correct drive (that would be sdc, say) 

To be ultra safe you can remove the internal drive first, though I never do it.

---

### Post by beew on 2011-04-01
This is a detail step by step tutorial for installing into an external drive or usb drive.
[URL="http://ubuntuforums.org/showthread.php?t=1494031"]
http://ubuntuforums.org/showthread.php?t=1494031[/URL] (post #7 by C.S.Cameron)

It is for 10.04, but it is the same idea for 10.10 except the squence of steps are slightly different. Important things to remember are installing into the correct target disk and make sure you install the bootloader correctly (in the target disk)

There is no need of the fat32 partition unless you want Windows to be able to access the drive, I also don't see why the /home partition needs to be in ext2. I would say format it in ext4. Finally, if you are careful you don't need to remove the internal drive.

---

### Post by horselover phat on 2011-04-01
Thanks very much dude! I have an external HD with very little on it, and a day old system image of my C:, so I'll try doing as you suggest.

Again, thanks!

---

