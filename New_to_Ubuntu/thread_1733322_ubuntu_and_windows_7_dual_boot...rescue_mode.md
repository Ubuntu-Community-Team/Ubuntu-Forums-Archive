---
title: "ubuntu and windows 7 dual boot...rescue mode"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by tusharbmw on 2011-04-19
Hi,

I used to dual boot my windows 7 and ubuntu.
But after grub 2 update, the system is going into rescue mode.

here is my fdisk output
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51b6df45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78142464    7  HPFS/NTFS
/dev/sda2            9729       24322   117216256    7  HPFS/NTFS


It looked like a common problem but to solve this i needed to update grub, but i am getting following error while trying to do so..
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


Can anyone assist?

Thanks and Regards,
-Tushar

---

### Post by sanderd17 on 2011-04-19
Hi there,

You cannot update grub like that from a live CD.

Can you show us the output of the bootscript? [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

(please put it between CODE tags, click on the #)

---

### Post by tusharbmw on 2011-04-19
Here you go:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   156,286,975   156,284,928   7 HPFS/NTFS
/dev/sda2         156,286,976   390,719,487   234,432,512   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       0dd41f5f-484d-4154-890f-615e488ac0b5   ext4                                     
/dev/sda1        2A60B09760B06AE9                       ntfs       OSDisk                        
/dev/sda2        A6D4B32FD4B3009B                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
```

---

### Post by sanderd17 on 2011-04-19
yetiman64 and you mentionned that you use WUBI.

WUBI is not a dual boot. You should not update grub on wubi, but that's the past.

I'm not used to wubi, so I can't really help you. But if you google your problem, be sure to use the term "wubi".

EDIT: as the script says: grub looks to partition #1 for it's files and wubi is in another (virtual) partition.

---

### Post by yetiman64 on 2011-04-19
tusharbmw, here is a link that might be helpful, [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198). Also it would pay you to put a reference to wubi in the thread title (you can edit it) to attract the attention of those with expertise in that area.

The bootinfo script that sanderd17 linked to is a very good idea as well. Link #1 in my sig has a guide for its use if needed, though there are instructions for its use from where you download it.

yetiman64

---

### Post by tusharbmw on 2011-04-19
Thanks guys, Lilo worked .and now I am able to boot windows.
I can see option for Linux also, but i am afraid if i boot linux it will again update to grub 2.
should i reinstall ubuntu using wubi? or there is any other solution to this?

really appreciate your help on this..
-T

---

### Post by yetiman64 on 2011-04-19
> **tusharbmw said:**
> Thanks guys, Lilo worked .and now I am able to boot windows.
I can see option for Linux also, but i am afraid if i boot linux it will again update to grub 2.
should i reinstall ubuntu using wubi? or there is any other solution to this?

really appreciate your help on this..
-T

Normally Lilo is only used to install an MBR to fix access to Windows, not to do a full Lilo install (it sounds like this is what you have done).

I can't really help too much more past this point sorry, but I will once again suggest you change the words "dual boot" in the thread title to "wubi install". This will help you much more than the current title in your circumstances. Cheers and good luck from yetiman64.

---

