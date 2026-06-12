---
title: "Having problems booting up Ubuntu"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Hallucinate on 2010-02-06
Okay I have windows 7 installed and ubuntu. I can't access grub on bootup it does the windows boot loader instead. How do i fix this? I have to use supergrub to boot into ubunu i've tried fixing with supergrub but to no avail. Please help.


Thanks.

---

### Post by oldfred on 2010-02-06
It sounds like you still have the windows boot loader in the MBR. Which version of grub do you have grub legacy (0.97) or grub2(1.97beta4) with a new install of karmic. The quick answer is to install grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you can get into your system with supergrub you can install grub2 from there.

reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub


If you need more help, this script will tell us about your system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

