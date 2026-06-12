---
title: "Install Ubuntu on external drive w/WinXP RAID array"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by hettsfield on 2010-03-21
I have a Windows XP computer with a RAID array.  ("with a RAID array" being the most important thing to note)

I tried to install Ubuntu 9.10 on an external USB drive.

Apparently GRUB messed up my MBR  because of my WinXP RAID array (according to some comments I read somewhere).  I had to go repair the MBR with fixboot and fixmbr, etc...


Now I'm back at square one.  I'm a linux noob and I'm crosseyed from reading.  

I can't figure out how to install Ubuntu to an external drive on a computer running WinXP from a RAID array....Please someone point me in the right direction....thx!!!

---

### Post by hettsfield on 2010-03-22
SOLVED....during installation I put the boot loader in the default hd0...that messes up the WinXP MBR.  you have to choose "advanced" and put the boot loader in the external drive.  also your motherboard BIOS has to support boot loading from usb drives.

---

