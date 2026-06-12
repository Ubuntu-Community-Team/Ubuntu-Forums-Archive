---
title: "[SOLVED] disk-error checking utility"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-16
Are there and disk-error checking utilities such as the one Windows has when you right-click on a disk and go to properties > tools?

This is the picture from windows, if I'm not making sense:

[IMG]http://www.pctechguide.com/images/tutorials/HDDMaint/Tools.gif[/IMG]

---

### Post by cdtech on 2008-12-16
There is a package called smartmontools that will check the drive for disk degradation and failure using the SMART system:
```
sudo apt-get install smartmontools
```
There is also a command called "fsck" that will check your disk file system for error's but that is run at boot and should indicate errors on bootup.

---

### Post by nhasian on 2008-12-16
each hard disk manufacturer provides their own tools to do error checking usually bootable CD/floppy image.  if you think you may have a problem with your hard disk, you should run their tests.

for example Western Digital has their Lifeguard data tools:

[http://support.wdc.com/product/download.asp?groupid=613&lang=en](http://support.wdc.com/product/download.asp?groupid=613&lang=en)

---

### Post by adobrakic on 2008-12-16
It's not anything in my system, it's my blackberry.

Would smartmontools work for checking my blackberry?

---

### Post by prshah on 2008-12-16
> **adobrakic said:**
> 
Would smartmontools work for checking my blackberry?

No smartmontools will not work in this case. For this case, see this [Re: Check Disk on SD/MicroSD Card?]("http://ubuntuforums.org/showthread.php?p=6330827&highlight=fsck+-a#post6330827")

---

### Post by adobrakic on 2008-12-16
thank you

---

