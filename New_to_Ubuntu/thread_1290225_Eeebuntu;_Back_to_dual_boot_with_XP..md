---
title: "Eeebuntu; Back to dual boot with XP."
date: 2009-10-13
forum: New to Ubuntu
---

### Post by tobiasolesen on 2009-10-13
Hi

I have a full install of Eeebuntu on my Eee PC 1000H which was pre-installed with windows. For various reasons I wish to go back to dual boot. 

I have a ghost image of xp on my computer with I can activate during the boot of eeebuntu. I tried doing this and it started installing xp again. The problem is that when I rebooted I got a grub load error of 13 or 17 which I am not exactly sure... 

I need a way to fix the grub loader so that it boots windows or make the windows boot-loader work. In this way I can setup windows and install Eeebuntu on the other partition.

I have done some research and tried finding a  solution. But I am not really sure that they will work as intended. I am not a computer wizard and need thorough description of what to do. 

Here is what I found picked up:

using fixmbr fixboot, by pressing R when asked to enter the recovery console... which I do not know what is.
[http://ubuntuforums.org/showthread.php?t=657592&highlight=grub+errror+13](http://ubuntuforums.org/showthread.php?t=657592&highlight=grub+errror+13) 


I am also thinking that I might be able to use a live usb disk after installing windows and then repair, erase or do whatever to grub in order to boot windows. I have no idea how to do this though.

At Grub loader menu I can press e at my ghost image and this reads:

rootnoverify (hd0,2)
savedefault
chainloader +1

I can not enter Grub loader menu after running the ghost image. I just get the grub load error.


Does anyone know how to do this?

Thank you

Tobias

---

### Post by carml on 2009-10-13
I think you can use a Live of Ubuntu or Gparted-Live to allocate the space you need for XP.I'd try in advance to fix Grub as someone suggested you.

---

### Post by Temposs on 2009-10-13
Alternatively, you could install Windows as a Virtual Machine, instead of messing around with all this master boot crap. It will be a lot simpler and more secure for your machine.

Open Applications->Add/Remove, search for Virtualbox OSE. You can install Windows on this and run Windows like a program. You can run all your Windows stuff without having to dual boot.

---

### Post by tobiasolesen on 2009-10-19
I have tried VirtualBox OSE a couple of times... I can't seem to access my ghost PE through it though... so I tried with another .iso image of windows xp. I get the attached error... any help?

\tobias

---

### Post by tobiasolesen on 2009-10-23
solved the problem by running the ghost image form the grubloader and then reinstalling eeebuntu which then included XP in the OS list.

---

