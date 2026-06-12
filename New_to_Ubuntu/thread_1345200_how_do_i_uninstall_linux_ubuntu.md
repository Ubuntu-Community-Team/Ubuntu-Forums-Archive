---
title: "how do i uninstall linux ubuntu"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by kokokiki on 2009-12-03
i want uninstall linux ubuntu but when i looked on the internet everything said chkdsk/f but i dont have a floppy disk all i have is the iso cd that i downloaded so what do i do ? 

and i dont have windows on just linux 

thanx for reading :D

---

### Post by marshmallow1304 on 2009-12-03
Install another OS over it.

---

### Post by Dvdre on 2009-12-03
I dual boot, so don't know if this is the same for you. But every time I have uninstalled -- before reinstalling -- I have used the Live CD and just deleted the Ubuntu partition and swap partition. Then I restarted and reinstalled to that empty disk space.

Depends on what you want to do when you uninstall, I guess. But if you delete those partitions, seems like you can install anything you want on the hard drive afterward.

---

### Post by jbrown96 on 2009-12-03
What do you mean by "uninstall" Ubuntu? Do you want to remove the OS, meaning you want the system blank (no OS at all)? 

If you just want to do that, then you can boot the LiveCD and run the following commands. 
WARNING! THIS WILL REMOVE EVERYTHING ON YOUR HARD DRIVE. ALL DATA WILL BE LOST!
1) Find the correct hard drive. Usually this is listed as /dev/sda, but it's a good idea to double check. In a terminal (apps-->accessories) ```
sudo fdisk -l
``` My system reports > 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e5f1410

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         851     6835626   83  Linux
/dev/sda2             852       19457   149452695    5  Extended
/dev/sda5            1703       19457   142617006   83  Linux
/dev/sda6   *         852        1702     6835626   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefcdbc7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux


You can see that there are two devices: /dev/sda and /dev/sdb; sda is the internal hard drive and sdb is an external drive. I can tell the difference based on the sizes that it reports (160GB for sda and 250.1GB for sdb). You need to determine which device to use. If you don't have any flash/external drives inserted and only one hard drive installed, then you should only get a single entry for /dev/sda.
2) Delete the data. WARNING! BACKUP ANY IMPORTANT DATA PRIOR TO RUNNING THIS COMMAND. ```
sudo shred -n 0 -zvv /dev/sda
``` replace /dev/sda with the proper device. This will write zeroes to the entire drive; nothing will be recoverable. If you need to securely wipe the drive (because you are getting rid of it), then you probably want to run this command instead ```
sudo shred -n 1 -vv /dev/sda
``` This will take much longer; it takes about 3 hours on my 250GB drive. 


If you just want to install another operating system, then you don't need to remove Ubuntu. You can just install the other OS. When you are installing the new one just delete all the partitions on the drive.

---

### Post by mjwilson1313 on 2009-12-03
Reinstall Ubuntu with the live cd or with another os cd.  Why do you want to remove it?

---

### Post by kokokiki on 2009-12-04
If you just want to install another operating system, then you don't need to remove Ubuntu. You can just install the other OS. When you are installing the new one just delete all the partitions on the drive.[/quote]
  
how i tried to insert 3 different windows installations and they all returned with error

Reinstall Ubuntu with the live cd or with another os cd.  Why do you want to remove it?

from where in the live cd when i open it it says those options 
try ubuntu without any change to your computer
install ubuntu
check disc for defects
test memory
boot from first hard disk

and the reason i want to uninstall it is because i accidentally deleted my partitions when i installed it and i think i could run a data recovering program in windows but not here and also whenever i try to setup a program there is these codes i have to write they work at first but always comes with an error at the end and i don't want to keep writing my programs forever maybe i would want to if the actually worked but i guess windows suits me best . but thanx for all ur help guys and if i dont find a program to recover my files i'll do as u said jbrown96

---

### Post by Terl on 2009-12-04
> **kokokiki said:**
>   
how i tried to insert 3 different windows installations and they all returned with error



If you tried per the above to install windows and received an error, it is not Ubuntu's fault.  What error did you get?  You should be able to install windows right over Ubuntu and it would be as if Ubuntu were never there.

If however, and I am guessing, you tried to install windows and keep ubuntu so you can recover some files like you allude too, that may be your problem - not enough drive space.

What errors did you get?

---

### Post by QIII on 2009-12-04
If you are trying to recover data before you do anything, then DO NOT install another OS over the top of whatever you have on there now.  You risk losing data completely.

I would recommend getting a copy of Photorec or using TestDisk from a live session of the LiveCD ("Use Ubuntu without making changes to your computer")

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

As for reinstalling Windows AFTER you recover your data, it may not be as easy as "just installing Windows".  The Windows installation my run away screaming when it sees extX partitions and tell you there is no room at the inn.

When you have recovered your data, it might be best to use the LiveCD to delete whatever partitions are there and create a single NTFS partition on the drive with GPartEd.

---

