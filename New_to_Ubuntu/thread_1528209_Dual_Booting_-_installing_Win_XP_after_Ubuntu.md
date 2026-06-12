---
title: "Dual Booting - installing Win XP after Ubuntu"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by ThisIDidNotDo on 2010-07-10
Hello, I hope this isn't too stupid a question and although it's similar to many that have been asked before, I can't find the answer to my exact problem.

I have an installation of Lucid Lynx which is working fine, but I now want to be able to dual boot with Windows XP.  I've made a primary partition (sda2) to install XP on, but when I run the windows installer it is unable to find any hard disks in my machine.  I have tried both fat and ntsc file systems on sda2 as well as leaving the space unpartitioned.  Any ideas?

I am expecting to have to reinstall grub once I'm done.

---

### Post by audiomick on 2010-07-10
I am not sure, but I think XP still had to go on the front partition of the drive. Could that be your problem?

---

### Post by ST3ALTHPSYCH0 on 2010-07-10
Steps are the same as [reply #10](http://ubuntuforums.org/showthread.php?t=1527888)

---

### Post by oldfred on 2010-07-10
Try NTFS and with gparted, right click manage flags put a boot flag on sda2. 

Windows can be installed to any primary partition, I just do not know if having the Ubuntu first confuses it.

Is it a SATA drive? I did not have issues with the version of XP I installed several years ago, but some have said you have to download the SATA drivers to get it to work.

Also in BIOS make sure you have drive set to legacy mode, PATA mode or not ACHI. I changed to ACHI and Ubuntu worked but my XP would not boot.

---

### Post by ThisIDidNotDo on 2010-07-10
Thanks for your quick replies - a few things to try there.  I'll get on it tomorrow and let you know if I'm successful.  Thanks!

---

### Post by sandyd on 2010-07-10
If your using a SATA drive, you are going to have to slipstream the SATA drivers onto the winxp cd. if the disc is winxp sp3, you do not need to do this.

---

### Post by john newbuntu on 2010-07-11
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by ThisIDidNotDo on 2010-07-11
Hey all, had a tinker again.

It is a SATA drive and I think this is the problem - *&^£ing windows!  The disks I have been failing with are SP2 and the original version of XP.  I'll track down a copy of SP3.

Thanks a lot, I can take it from here.  Amazing responses, thank you!

---

