---
title: "Made an error using WUBI"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by dgub on 2009-09-08
I am new to Linux. 

I have just installed 8.04 on a seperate partitioned HD. Having burnt the ISO I was then offered to install from Windows. I was expecting it to create and ext3 partition but instead has used the existing NTFS partition.

I did not think to check this and once rebooted I continued to upgrade to 8.10. Is there a way to convert to ext3 without losing the upgrade data please, or do I have to do another fresh install from Ubuntu. I was wondering if I backed up or imaged the partition first whether it would transfer across.

Another question is the size of the partition. In Windows I have only the essential files on the boot disk which gives me a small 4GB partition to back up. I see with Ubuntu that it is already at 18GB ignoring the swap disk. Is possible to seperate the files in the same way in Ubuntu.

Thanks

---

### Post by bodhi.zazen on 2009-09-08
Yes it can be converted, but it is not easy.

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Yes, you can resize your Ubuntu partitions if you wish. I typically give my linux / partitions 10 Gb.

You may further sub divide if you wish, put / on a separate partition form /home is common, but it can get complicated.

---

### Post by dgub on 2009-09-08
> **bodhi.zazen said:**
> Yes it can be converted, but it is not easy.

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Yes, you can resize your Ubuntu partitions if you wish. I typically give my linux / partitions 10 Gb.

You may further sub divide if you wish, put / on a separate partition form /home is common, but it can get complicated.

Thank you for that. I will try and work my way through that.

---

### Post by dgub on 2009-09-10
That was fairly straightforward and easy to follow, but it did not work.

I transferred it to the front of another HD and it all seemed to work ok but on reboot it went back to the WUBI install. The boot menu was not changed. It also deleted the remainder of the partitions on the drive which I then had to spend some time recovering. This could have been caused by using Paragon HDM to create the partitions instead of using Linux.

Tried it again and still would not boot into the new disk.

I have a spare drive from Seagate (warranty claim), so put that on and reverted to the 8.04 install. This went ok but again it would still boot into the WUBI install. From XP I un-installed the Ubuntu install and installed the 8.04 again. Now it just boots straight into Windows. There is no boot menu.

This is being installed on the fourth HD.

Would appreciate some help in getting this to install please.

---

### Post by dgub on 2009-09-10
Just to update this. I can get into Hardy by pressing F8 from the BIOS boot menu and choosing an alternative drive. I would have thought that it would have known which was the boot drive.

So now I need a method of changing it to the correct drive please.

---

### Post by bodhi.zazen on 2009-09-10
It sounds as if you will need to edit /boot/grub/menu.lst to point to the correct drive.

This is the root (hdx,y) line.

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

You probably need to change (hd0,x) to (hd1,x) or similar.

---

### Post by dgub on 2009-09-10
> **bodhi.zazen said:**
> It sounds as if you will need to edit /boot/grub/menu.lst to point to the correct drive.

This is the root (hdx,y) line.

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

You probably need to change (hd0,x) to (hd1,x) or similar.

Thank you

There is not a problem with partitioning, but there does seem to be an inconsistency with the naming of the drives. Having taken great care in GParted to correctly format the correct drive, make a note of the of the identifier, ie sdc etc. This followed logically in the order listed in the BIOS. When it came to installing 8.04 in the correct drive it then chose to format the wrong one, hence trashing the info on that disk. In reading around this forum it seems others have had similar problems and the only safe would appear to remove all other drives.

I am rapidly going off Ubuntu and Linux. It has caused more damage in a few hours than Windows has ever done.

---

### Post by bodhi.zazen on 2009-09-10
Any OS will cause such damage and installing a new OS is a major change to your computer.

When installing you need to understand partitioning and partitions are identified differently in windows, linux, and grub.

C:\ == /dev/sda1 == (hd0,0)

Usually the default settings work just fine and IMO most of the problems occur when people start making changes to the defaults, such as switching or removing hard drives, when they install. You run into problems when you change your hardware configuration as when you install your HD is (hd0,0) or /dev/sda1 , but now replace your windows drive and suddenly either windows can not boot , as c:\ no longer exists (in the bios) or Ubuntu can not boot as the ubuntu drive is not (hd1,0) or /dev/sdb1. You see, you can easily cause the problem because you changed the hard ware.

Put you windows drive as "Master" , your Ubuntu drive as "slave" , install Ubuntu to the slave drive, install grub to the master drive, and do not change your hard ware, either physically or in the bios. (when you boo the second drive in the bios it gets more interesting as it may well become (hd0,0) and /dev/sdb1 !!! ).

I am not saying this is the cause of your issues, just warning you.

I would also advise you that just as you did not learn Windows in a day, it takes time to learn a new OS and boot loaders are complicated. for example, do you even know how to configure the windows boot loader to boot Ubuntu ?

If you are causing "damage" to your system it is an indication you need to stop for a minute and understand what you are doing and why. If you have questions , please ask.

---

### Post by dgub on 2009-09-10
> **bodhi.zazen said:**
> Any OS will cause such damage and installing a new OS is a major change to your computer.

When installing you need to understand partitioning and partitions are identified differently in windows, linux, and grub.

C:\ == /dev/sda1 == (hd0,0)

Usually the default settings work just fine and IMO most of the problems occur when people start making changes to the defaults, such as switching or removing hard drives, when they install. You run into problems when you change your hardware configuration as when you install your HD is (hd0,0) or /dev/sda1 , but now replace your windows drive and suddenly either windows can not boot , as c:\ no longer exists (in the bios) or Ubuntu can not boot as the ubuntu drive is not (hd1,0) or /dev/sdb1. You see, you can easily cause the problem because you changed the hard ware.

Put you windows drive as "Master" , your Ubuntu drive as "slave" , install Ubuntu to the slave drive, install grub to the master drive, and do not change your hard ware, either physically or in the bios. (when you boo the second drive in the bios it gets more interesting as it may well become (hd0,0) and /dev/sdb1 !!! ).

I am not saying this is the cause of your issues, just warning you.

I would also advise you that just as you did not learn Windows in a day, it takes time to learn a new OS and boot loaders are complicated. for example, do you even know how to configure the windows boot loader to boot Ubuntu ?

If you are causing "damage" to your system it is an indication you need to stop for a minute and understand what you are doing and why. If you have questions , please ask.

Thanks

Sorry about the rant but it had really got to me.

Master/slave does not work with SATA drives. It would appear that it is not consistently identifying the drives. It should be in the order as in the BIOS but that did not happen.

---

### Post by bodhi.zazen on 2009-09-10
> **dgub said:**
> Thanks

Sorry about the rant but it had really got to me.

Master/slave does not work with SATA drives. It would appear that it is not consistently identifying the drives. It should be in the order as in the BIOS but that did not happen.

I would check to see if there is an update to your BIOS then. I have never had this problem with my SATA drivers (3 systems with multiple SATA drives).

---

### Post by dgub on 2009-09-10
I don't think it is a problem with the BIOS. When I use GParted I am assuming that it is listing the drives as seen by the BIOS, however in Windows I have much more information to make sure I am selecting the right drive, as shown in this screen-shot which is part of Paragon. Is there an equivalent in Ubuntu please.

---

