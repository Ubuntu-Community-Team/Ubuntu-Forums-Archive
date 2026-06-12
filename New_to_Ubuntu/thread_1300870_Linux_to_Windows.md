---
title: "Linux to Windows"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by gavdari on 2009-10-25
hi everyone
first of all, Linux is a wonderful OS, but not for me. maybe for someone who got his first computer with ubuntu. I installed ubuntu about a month ago and I had problems with absolutely everything since then. my last problem was with GRUB. I had a dual boot system with win XP and all of a sudden I got hal.dll error when tried to boot to windows. I tried many things but nothing answered. last night I was trying to work things with grub, so I used setup command on grub commandline and I installed it on my first drive, the one with windows on it. it didn't solve the problem, so I tried to roll back to windows. I formatted my hard drive with windows on it and installed windows again with no problem. but when I first entered windows, I saw that my another harddrives is indicated as unallocated drive. I need a way to recover those data. I'm sure that I never formatted the drive that is now missing.
what can I do?

---

### Post by halitech on 2009-10-25
if you now have windows running you could try using SuperGrub to get back into your ubuntu install. Supergrub can be found here [http://www.supergrubdisk.org](http://www.supergrubdisk.org)

Grub and Ubuntu have nothing to do with windows other then grub doing the boot loading for both OSes so reinstalling grub won't fix windows dll errors.

If you want to read your files from Windows, it won't read ext2/3/4 natively so you need external software. You can try [http://www.fs-driver.org/](http://www.fs-driver.org/) but I'm not sure it supports ext4 so if its in ext4, you need to get booted back into Ubuntu to recover the data.

---

### Post by LewRockwell on 2009-10-25
drives...or partitions?

possible recovery via Testdisk and/or Photorec

you can find those amongst the utilities on Parted Magic LiveCD Utilities Disk

[http://partedmagic.com/](http://partedmagic.com/)

.

---

