---
title: "can I download Ubuntu on external drive"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by bootneck02 on 2010-09-07
):PI have upgraded my PC and am running Windows 7 Pro 64Bit and would like to run Ubuntu 64 Bit (because I would like not having to keep filling Microsoft's coffers also I understand that Linux is more secure than Windows). I have only used Windows so this would be a new adventure for me. :D I do not want to dual boot so is it possible to download onto a external drive and run from that whilst I learn how to use the OS?

---

### Post by Arla on 2010-09-07
You can, for starters though I'd suggest running it as WUBI (unless you have deep resentment of doing that) to try to check that a) it works for your hardware and b) you're interested in investing the time to learn it.

---

### Post by 0N3 on 2010-09-07
Go here to make your HDD Bootable 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I also have a tutorial on youtube on how to do it. Pause the video as you go along to follow the steps and preferably watch it in fullscreen mode and HD

My youtube video: [http://www.youtube.com/watch?v=iDr-rnz1WTQ](http://www.youtube.com/watch?v=iDr-rnz1WTQ)

---

### Post by cake nom nom on 2010-09-08
> **Arla said:**
> You can, for starters though I'd suggest running it as WUBI (unless you have deep resentment of doing that) to try to check that a) it works for your hardware and b) you're interested in investing the time to learn it.

[http://wubi-installer.org/](http://wubi-installer.org/)

give it a try, it's like your everyday windows program which you can install and uninstall under (im not sure about windows 7 but in xp) add/remove programs in the control panel

---

### Post by dirghrabadia on 2010-09-08
I would prefer burning a Live CD/USB, and trying it from there, since I had some issues with WUBI when I ran it on Vista.

---

### Post by 3rdalbum on 2010-09-08
Installing Ubuntu onto an external hard drive is, basically, dual-booting.

If you decide to boot up the CD and install to your external disk, then make sure you click the "Advanced..." button that appears after the partitioning screen, to install the bootloader onto the external hard disk. When you click the Advanced button, it will allow you to specify a path to the disk where you want the bootloader installed.

You must specify the device file name; basically at the earlier screen where it asks you where you want Ubuntu installed, it says the device file name in brackets; for instance: "Erase entire disk (/dev/sdb)". Whatever the device file name ends off being, put it into the field for the bootloader.

Then when the installation is complete, you will need to go into your computer's BIOS to tell it to boot up from the external hard disk rather than the internal.

If you were installing Ubuntu to your internal disk, then you wouldn't need this step.

---

### Post by ugm6hr on 2010-09-08
3rdalbum's advice is spot on.

I'd just like to reiterate that you should pay attention at the stage:
> **3rdalbum said:**
> "Erase entire disk (/dev/sdb)". 

Obviously, you should ensure that you erase the external, not the internal, disk. Simple enough to tell which is which, particularly if they are different sizes.  But ask at that point if you are not sure.  The output from the command below can help, alongside your physical description of how big the drives are, and how they are set up.
```
sudo fdisk -l
```

---

### Post by mastablasta on 2010-09-08
now that we all probably scared the sh... out of you with all the commands and al,l that i suggest you read this nice little FREE e-book that you will find here: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
 
Especially page 11 onward for instalation. But the rest is good read too with lot's of pics.

---

