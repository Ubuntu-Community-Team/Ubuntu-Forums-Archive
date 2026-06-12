---
title: "Problems detecting IDE/SATA Hard Drives"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Zeroberry on 2008-12-14
The title is a little misleading. You see, I have two hard drives, one plugged in by a good old IDE and one by SATA. The SATA one has Windows on it and the IDE one has ubuntu. When I boot in Windows I can only find the SATA hard drive and when I boot in ubuntu I can only find the IDE one... I've tried pretty much everything I can find. Basically ubuntu seems to be unable to detect the hard drive with windows. Is this a simple problem and I'm just stupid or what? I've done my best to find an answer myself but no luck, so got myself registered.

I hope some genius out there can help me out. Thanks for reading!

---

### Post by gettinoriginal on 2008-12-14
Sure it can be done. The one problem you may encounter is the GRUB installer makes a guess as to which drive is 1st in boot order and installs a pointer to the grub program in that drives MBR.
Sometimes it guesses wrong. (seems that this is a problem only if the PC has a mix of ide and sata drives).

The machine boots straight to windows you never see the grub menu.
You can use BIOS to switch boot order or you can alter the MBR of the 1st drive to load GRUB instead of window. May want to look at this thread before you begin. 

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Good Luck :p

---

### Post by Moop on 2008-12-14
Windows won't see your Ubuntu hdd by default. You can install Ext2 IFS in windows so it can use ext3 file systems. 

Did you have the windows hdd unplugged when you installed Ubuntu?  See here to mount windows. [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Zeroberry on 2008-12-15
Ah no, I get the GRUB. I can boot in both ubuntu and windows, no problems there. It's just that the ATA hard drive doesn't exist when I'm in ubuntu.

Now I've discovered a new problem too, I can't remove that hard drive, unable to boot at all. grub error.

---

### Post by caljohnsmith on 2008-12-15
How about booting your Live CD, download the attached "boot_info7.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info7.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by Zeroberry on 2009-01-04
Whatever my problem was, a clean install of alternate version 8.10 Ubuntu sorted it out. I can now access the NTFS formatted partition and the proprietary drivers work!

Thanks for the help anyway!

---

