---
title: "grub not finding Win 7"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by crip720 on 2011-07-03
Hi, I have a Windows7 partition on my harddrive, but I installed a torrented copy of Win7 Ultimate over it.  I restored grub2 v1.98 to my harddrive and did the update for grub.  Grub will find all my partitions[OS x] on internal and external drives, but it will not find[access] the Win7 partition.  It will locate the Win Recovery partition.  The error is  " ls: cannot access /media/ACER windows/boot", plus "Boot: No such file or directory".  disk is show sda2 as boot, which is the Win7 partition.  I restored grub with Boot-Repair,  plus I also reinstalled grub with Synaptic.  The error is on grub update[see above].  Any help will be appreciated.  Thanks Colin.

---

### Post by wildmanne39 on 2011-07-04
> **crip720 said:**
> Hi, I have a Windows7 partition on my harddrive, but I installed a torrented copy of Win7 Ultimate over it.  I restored grub2 v1.98 to my harddrive and did the update for grub.  Grub will find all my partitions[OS x] on internal and external drives, but it will not find[access] the Win7 partition.  It will locate the Win Recovery partition.  The error is  " ls: cannot access /media/ACER windows/boot", plus "Boot: No such file or directory".  disk is show sda2 as boot, which is the Win7 partition.  I restored grub with Boot-Repair,  plus I also reinstalled grub with Synaptic.  The error is on grub update[see above].  Any help will be appreciated.  Thanks Colin.Hi, boot ubuntu and just run
```
sudo update-grub
```
if that does not work, post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

