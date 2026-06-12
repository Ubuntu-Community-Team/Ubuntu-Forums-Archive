---
title: "won't boot"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by protpisys on 2010-08-19
Hey, I'm a beginner here and am running Ubuntu and Vista side by side, at least for a while. When I start the computer I occasionally get the screen with the error message " error: no such device: fddadbd2-6b65-4065-9051-91528415684a" with a prompt that reads "grub rescue"  usually I can just shut the computer off ans start it right back up and it goes to the screen where you pick Ubuntu or Windows, but today I get the above and reboot like 10 times but still keep getting the error and grub deal. What can I do? Is there something I can do to make it stop? I'm using a Toshiba Satellite, it's so bad today I had to use the disc to get it to work at all.

---

### Post by opto09 on 2010-08-19
I don't know if this helps but have you looked at the manual? [http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

If that doesn't help we'll need more information like what version of grub and Ubuntu you're running? Also did you recently upgrade it from a different version?

---

### Post by protpisys on 2010-08-19
I had no idea I was running any grub at all, I have no idea what it is...I running the latest version...10

---

### Post by wilee-nilee on 2010-08-19
From a Ubuntu environment run the bootscript in my signature, and post it in code tags as described.

---

### Post by protpisys on 2010-08-19
> **wilee-nilee said:**
> From a Ubuntu environment run the bootscript in my signature, and post it in code tags as described.
ok, thanks...I downloaded the boot info and got this:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   488,396,799   485,322,752   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4EC25B71C25B5C71                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        C6848ACA848ABC85                       ntfs       SQ004668V05                   
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by protpisys on 2010-08-19
> **protpisys said:**
> ok, thanks...I downloaded the boot info and got this:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   488,396,799   485,322,752   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4EC25B71C25B5C71                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        C6848ACA848ABC85                       ntfs       SQ004668V05                   
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb
could it be that I installed Ubuntu originall with an external drive and it doesn't seem to be finding it?

---

### Post by protpisys on 2010-08-19
That must of been it I wiggled some wires, and rebooted the drive and my 'puter and all is well. Thanks for the direction.

---

