---
title: "boot linux from windows"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by PMxD46 on 2010-12-15
I have Windows 7 and ubuntu installed. But when I installed windows, it would no longer boot linux.. I have serched the internet, and have tryed to use this [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux), but it wont work. 

I have read a place that if I reinstall linux, my windows bootloader will disapear, and I can't acces windows.

how can I make my windows bootloader to boot linux ?

---

### Post by Timo0060 on 2010-12-15
This is a weird problem. On my laptop I have windows 7 and Fedora, I use to have Kubuntu, and the windows bootloader recongnized Kubuntu, and the Kubuntu bootloader reconginzed the windows bootloader as an option to choose, so i would just choose that option to go to windows bootloader then boot 7 from there. Wow.... run on sentence.

---

### Post by Medivh90 on 2010-12-15
If you have been first installed ubuntu than windows now should working. 
         -   if windows do not work just insert install disk in the section when need's to be installed press r to repair, when it takes you to console enter 'fixboot' and 'fixmbr'

That is for windows now, you can do what you want but i will tell you friendly with advice, use grub, just insert ubuntu live cd re isntall grub and that add windows to grub list, so than you will have grub who point to widnows and linux where you can choose what system do you want to use. (Do not try to do this if you have to old computer- mainboard)

Complete tutrorial how to set up grub is here: 
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by tajiknomi on 2010-12-15
> **PMxD46 said:**
> I have Windows 7 and ubuntu installed. But when I installed windows, it would no longer boot linux.. I have serched the internet, and have tryed to use this [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux), but it wont work. 

I have read a place that if I reinstall linux, my windows bootloader will disapear, and I can't acces windows.

how can I make my windows bootloader to boot linux ?

[SIZE=2]When you install WINDOWS after Linux, it will ***overwrite*** your MBR, the only fix for that is to ***reinstall Grub***...and this is easy...>[/SIZE][https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Direct method(Steps) >  [http://ubuntuforums.org/showthread.php?t=1644428](http://ubuntuforums.org/showthread.php?t=1644428)

---

### Post by mastablasta on 2010-12-15
> **PMxD46 said:**
> 
I have read a place that if I reinstall linux, my windows bootloader will disapear, and I can't acces windows.
 
how can I make my windows bootloader to boot linux ?
 
is there any specific reason you need the windows boot loader?
 
Linux will replace windows main boot record (MBR) with GRUB (which is linux boot loader). as long as your install is not wubi. 
 
you can change settings for grub as well. and it will be able to boot your windows. it's just that first thing computer (and users) sees will be grub and then you select in grub what you want to be loaded. DOS, windows... whatever you want. when you choose windows i think you will still be able to get to widnows boot menu by pressing F8 and choose safe mode, command line mode or anything else you might want to choose.
 
grub can be updated, replaced, edited, customized (for example put some background to it so it's not all black) whatever you want....

---

### Post by NCLI on 2010-12-15
> **PMxD46 said:**
> I have read a place that if I reinstall linux, my windows bootloader will disapear, and I can't acces windows.

That is not true, reinstalling Ubuntu will no remove you Windows bootloader, although reinstalling Windows will remove the Ubuntu bootloader, but that's just because Microsoft thinks Windows is the only OS you should ever want to use. :p

---

### Post by Mark Phelps on 2010-12-15
> **NCLI said:**
> That is not true, reinstalling Ubuntu will no remove you Windows bootloader, although reinstalling Windows will remove the Ubuntu bootloader, but that's just because Microsoft thinks Windows is the only OS you should ever want to use. :p

BOTH of the first two remarks are untrue! As to the third -- who knows, maybe.

In BOTH cases, what gets replaced is the MBR -- NOT the bootloaders.

However, since the MBR invokes a default boot loader, it LOOKS like the boot loaders got replaced when, in fact, they did not.

---

