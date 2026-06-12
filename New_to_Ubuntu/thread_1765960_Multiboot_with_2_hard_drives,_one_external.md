---
title: "Multiboot with 2 hard drives, one external"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by TheCoon on 2011-05-23
Hi,
I have Windows XP Pro installed on a 250GB internal drive, with another 750GB internal drive used for extra storage. 
I also have a new Verbatim 1TB external drive (powered, USB), and this drive will be hooked up to my PC most of the time.

I've installed Ubuntu on the external drive, and I want to edit XP's BOOT.INI to add an entry for Ubuntu on the external drive. How do I point to the external drive in order to add this option? 

Currently my BOOT.INI looks like this:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```

So I want to add an option to boot Ubuntu from the external drive, which will be connected to my PC almost always. 
BTW, the idea behind this is that I will be able to (when needed) take my external drive, hook it up to a different PC and still be able to boot from it (any thoughts on this are also welcome). 
But first of all, I need to be able to (selectively) boot from my current machine.

Thanks for any help :)

---

### Post by yetiman64 on 2011-05-24
This link following is from 2005 (old info) but may be of use to you if you have a floppy disk drive available.

[U]**--**[**How to dual boot Ubuntu and Windows XP without changing the Windows MBR--**]("http://ubuntuforums.org/showthread.php?t=56723")

[/U]Read fully and carefully before trying.

---

### Post by TheCoon on 2011-05-24
Any idea how I can do something similar if I've already installed Ubuntu on my second HD? Google yielded no results on this...

---

### Post by oldfred on 2011-05-24
You just want to have the grub2 bootloader installed to the external drive which should let you boot it anywhere as long as proprietary video drivers are either the same or not installed.

If you set BIOS to boot external first it will boot grub and give you a choice of what to boot. If you unplug the external then it defaults to the windows boot loader in the MBR of the internal drive and boots windows.

My example is for an install in sda5 and installing to sda. You need to find partition with Ubuntu sdbX and use that in the mount command and install to sdb.
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

