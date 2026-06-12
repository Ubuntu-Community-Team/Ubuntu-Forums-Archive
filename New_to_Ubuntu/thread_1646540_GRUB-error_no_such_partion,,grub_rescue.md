---
title: "GRUB-error no such partion,,grub rescue"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by caroulx on 2010-12-16
Hello guys..im really2 need help here..im new to this..soo sorry..my situation is i had dual boot..first boot that have linux and my xp..then after i pick the xp it show the second boot..that contain 2 xp that i hav to choose...my problem is i want to remove the linux..i just remove the partition throughh disk mngmnet and i format it..after that i use windows recovery console and do the "fixboot" and "fixmgr"..then i restart..suddenly it pop up error like this..
error: no such partition.
grub rescue>

pliz help me guys..im totally noob about this..i dont know how to fix this.i'l already ggogle it but dont find the solution..im just want to get my xp back!!im realy2 apreciate for your help guys..help me!!thx ...

im using xp sp3..and the newest ubuntu 10.10...

---

### Post by wilee-nilee on 2010-12-16
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

This will give us the lowdown on what is where.

---

### Post by caroulx on 2010-12-16
ok..here's the result igot it...thx
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 16128.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,126   244,199,423   244,183,298   f W95 Ext d (LBA)
/dev/sda5              16,128   183,317,958   183,301,831   7 HPFS/NTFS
/dev/sda2    *    244,199,424   488,395,119   244,195,696   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        5C9E69E69E69B8E2                       ntfs                                     
/dev/sda5        F87CAA667CAA1EFE                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader]  
timeout=30  
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS  
[operating systems]  
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professionalku" /fastdetect  
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP 2" /fastdetect 
```

---

### Post by wilee-nilee on 2010-12-16
You have a setup that I wonder if it will work even if the mbr is reloaded sda1 is a extended sda5 is a ntfs and the last partition is sda2 the bootable one. 

Grub 2 is installed in the **MBR** of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

To replace grub here is a link.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by caroulx on 2010-12-16
so what should i do?im totally noob here..i dont understand at all..where should i replace the grub?i dont understand..sorry..huhu..

---

### Post by Medivh90 on 2010-12-16
Hi, if you cannot boot windows, and ubuntu neither, that use windows install disk go to repair and enter fixboot and fixmbr
Than you should be in a situation of working and booting xp without a sign of ubuntu.
Now when you done with this, take a ubuntu live CD(10.10,10.04 or 9.10) insert, boot, try ubuntu, 
now you need to fix grub2
look at this topics
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://ubuntuforums.org/showthread.php?t=1200326](http://ubuntuforums.org/showthread.php?t=1200326)
[http://ubuntuforums.org/showthread.php?t=1645950](http://ubuntuforums.org/showthread.php?t=1645950)

follow instructions for grub2 reinstalling.

---

### Post by caroulx on 2010-12-16
do you mean that i must reinstall the ubuntu 1st?then fix the grub?and i already did the fixboot and fixmbr..still not working..

[SOLVED]THX U GUYS!!!I made it!!Now i can boot my xp again..thx!!i really appreciate it!!Good work guys!!!:)

---

### Post by Medivh90 on 2010-12-17
> **caroulx said:**
> do you mean that i must reinstall the ubuntu 1st?then fix the grub?and i already did the fixboot and fixmbr..still not working..

[SOLVED]THX U GUYS!!!I made it!!Now i can boot my xp again..thx!!i really appreciate it!!Good work guys!!!:)

No as i said, first fixboot and fimbr, you have now xp working.

But just you should know, there is probably still ubuntu on other partition but you cannot access it. If you want to restore ubuntu and to have ubuntu and xp parallel you must folow these links to re install grub2. (Insert live CD, go to terminal..) 
If that guide does not work you can be in situation to xp and ubuntu do not work, than again fixboot and fixmbr...

On other side if you do not need ubuntu anymore you can just launch some program for partitioning and format to NTFS ubuntu partition, that is just to don't have waste of hard disk space, this is if you wish.

---

