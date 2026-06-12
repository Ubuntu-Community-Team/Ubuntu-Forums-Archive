---
title: "moving ubuntu from second hard disk to first"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by joe2005 on 2010-01-17
My PC is provided with Two hard disks.On first XP is installed.On second Windows 7 RC and Ubuntu 9.10 are installed.Earlier when 9.04 was working booting was fast.But when 9.10 installed grub boot is painfully longer.My guess is that shifting Ubuntu from second to first disk may  cause grub to boot quickly.To go about in shifting I request technical guidance as I am a newbie yet to come to terms with ubuntu.First of all is my surmise is right?
Kept ready unallocated space in first disk though it is about 2GB short of the existing ubuntu partition.Reqest advise.thanks

---

### Post by SuperSonic4 on 2010-01-17
You can but there will be negligible speed increase because grub still has to look on both drives

---

### Post by Paqman on 2010-01-17
Your problem is due to a bug in Grub2, which is now the default bootloader in 9.10. If it's a pain then you can switch back to Grub Legacy.

---

### Post by oldfred on 2010-01-17
There is a minor bug in grub2 where multi drives are involved. It takes about 20-30 seconds extra while it scans drives

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

If you have a separate /home your should only need10-20GB to install Ubuntu to the other drive.
Move home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 
[https://help.ubuntu.com/community/Pa...ng/Home/Moving](https://help.ubuntu.com/community/Pa...ng/Home/Moving) 
[http://embraceubuntu.com/2006/01/29/...own-partition/](http://embraceubuntu.com/2006/01/29/...own-partition/)

---

