---
title: "Help to get NTFS system back."
date: 2010-01-28
forum: New to Ubuntu
---

### Post by Locaj on 2010-01-28
Hi.
 
Complete noob here.
 
Long story short. I had windows system on separate drive wanted to switch between them using BIOS boot menu. after installed Ubuntu on separate IDE drive (which failed btw) i cant load Windows XP from my main SATA drive. I get GRUB error and GRUB rescue.
 
 
Now wall of text.
I got 3 drives. 2 sata and 1 ide. Both sata got separate its own WinXP, sata1 have SP3, sata2 have SP2. I choose between them from BIOS boot menu only. IDE was meant to be for ubuntu. When i tried install ubuntu 9.10 from live cd i disconnected both sata drives so that ide was only drive in pc. I installed all and when ubuntu was loading after install i got error msg "usr/lib/libgconf-sanity-check2 exited with status 256". I read somewhere that i can try to set permission to that file but i ran ubuntu from live cd and had no permission to change this file as it was not this user.
Than i thought i done wrong by disconnecting sata drives. So i connected sata drives back and installed ubuntu again on same disk (ide) i got the same gnome error. 
Now i cant load system from my main WinXP drive.
 
I think boot table was changed but have no ide how to fix it.
Please help me, i know its actually winxp problem but the second problem with gnome got twice now...
 
Ohh and when the gnome error shows i press Close and than he askes me to choose user and password, than shows error again and in a loop. I cant see desktop or nothing.
 
I got in deep sh*t now.
 
Please help.
 
Thanks!

---

### Post by Leppie on 2010-01-28
i don't know about the gnome error, but you can restore the mbr of your windows disk using the ubuntu livecd:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by oldfred on 2010-01-28
Leppie's way is good if your Ubuntu is working.

Alernative if you can not run from Ubuntu.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I would try this from a terminal, just to make sure your system is up to date:
apt-get update
apt-get upgrade
sudo apt-get install --reinstall ubuntu-desktop

---

