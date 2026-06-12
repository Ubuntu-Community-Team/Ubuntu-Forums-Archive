---
title: "Grub error 21 when I unplug USB Hard disk"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by rhinokh on 2009-08-15
Hello,

I am a new user for ubuntu. My laptop got Vista and I want to install Ubuntu on my USB external hard disk. After the installation, I got grub for choosing the operating system to run but the problem is that when I unplug my USB external hard disk, the grub is error in number 21. I cannot run my vista without plugging my external hard disk. Can anyone help to solve it? I want to boot my Vista without plugging my external hard disk so I can use my laptop as usual....

---

### Post by Gone fishing on 2009-08-15
Ok seen this before - You installed with the USB in the drive and when grub installed it named the drives and partitions. If you remove the USB drive grub can't find the root partition.

Have a look at this [http://ubuntuforums.org/showthread.php?t=1183901](http://ubuntuforums.org/showthread.php?t=1183901)

I think it will help you with your problem

---

### Post by oldfred on 2009-08-15
You have several choices,depending on what you want. You will have to fix the windows boot on your windows drive. You can add a /boot or /grub partition to your windows drive, it only has to be 100mb with grub so you have menu.lst to choose windows or choose the USB drive if plugged in. You could create boot floppy or boot CDs. 
Best may be to use windows to FIXBOOT your windows drive and in BIOS make the USB drive the first boot drive and install GRUB to the USB drive. That way if the USB drive is not installed it will boot from your windows c: drive, if it is installed it will boot from the USB drive. 

Some info here:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

