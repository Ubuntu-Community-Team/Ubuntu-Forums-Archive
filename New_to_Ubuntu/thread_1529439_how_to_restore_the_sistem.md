---
title: "how to restore the sistem"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by valllllll2000 on 2010-07-12
Hi everybody,

I am not sure about the right section...

I just bought a samsung n150 netbook. I have installed ubuntu 10.04 netbook version. The problem is I have lost the windows 7 partition, the recovery and all there is now only one partition: ubuntu. Is there something I can do to restore windows 7 (restore to pre-partition step and preinstallation) and later reinstall ubuntu to have them both? I have talked to samsung and they said I have to pay a workshop to reinstall but I would like to know if there maybe another solution??
please help 

thank you very much in advance

---

### Post by mastablasta on 2010-07-12
by calling Microsoft and giving them the number (of Win) you should get a free recovery CD if i understand their policy correctly. That CD can then be used to install the windows back on.

---

### Post by valllllll2000 on 2010-07-12
thank you mastablasta I will try that

---

### Post by valllllll2000 on 2010-07-12
hi,
before contacting microsoft I am trying to restore the boot table. with testdisk,
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

this is what the anlisis brings me:
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D Linux                    0  32 33 19086 158 16  306624512
D HPFS - NTFS           1958  64 27  1971   0 13     204800 [SYSTEM]
D HPFS - NTFS           1971   0 14 10364  42 46  134836224
D HPFS - NTFS           7192 170 19 19457  21 20  197027840 [TEMP_PART01]
D HPFS - NTFS          10364  42 46 18757  85 15  134836224
D Linux                10364  42 47 11579 237 34   19531248
D HPFS - NTFS          10364  42 47 19457  21 20  146077696
D Linux Swap           19086 190 49 19457  53 36    5951472


So I am not sure which one to restore and which one to put as bootable anybody has experience with this tool?

---

### Post by lukeiamyourfather on 2010-07-12
Is the Windows partition still there but just not bootable? When you say its "lost" how exactly did you discover this. Its possible that you just need to setup GRUB to see the Windows partition in addition to the Ubuntu partition.

---

### Post by valllllll2000 on 2010-07-12
no lukeiamyourfather the partition is DELETED as you can see the D in front of them. I installed ubuntu and deleted the previous partitions by mistake and I want to reconstruct the previous partition table ( i will reinstall ubuntu later it's not a problem). Here is what I know. Before I installed ubuntu there was:
-one partition C win7
-one partition D also win7 (i don't really know what was there)
-one partition recovery
-one partition samsung diangnostics or something like that. 
So in testdisk i can reconstruct the partition table but I have to change the D in front of some of the windows partitions you see on the list i posted previously. 
so the options for each partition are:
Logical
primary bootable
primary
deleted
extended....
so which one should be logical, bootable.... ect?
I think that the original C: should be bootable but about the others I have no idea... anyhelp?
thnks in advance

---

### Post by audiomick on 2010-07-12
Hi.
It might be worth running the boot info script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

The results.txt file it produces provides pretty comprehensive info about what is on the computer and the boot setup. Post the results.txt here, and maybe someone can make a suggestion on the base of it.

---

### Post by valllllll2000 on 2010-07-12
here is what I get<.
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,626,559   306,624,512  83 Linux
/dev/sda2         306,628,608   312,580,079     5,951,472  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        eb142885-539e-4c35-adf7-c3944cd0039d   ext4                                     
/dev/sda2        9d50cca5-a868-42d4-9b2f-ee0dba7ec304   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
 do you need more info? the file had more details,,,, thks a lot

---

### Post by audiomick on 2010-07-12
Hallo.

sorry, I think it was a bad tip... :(

Your post #6 wasn't there as I posted, and the results.txt shows exactly what you said there, i.e. the windows partitions are gone. I had thought, on the basis of lukeiamyourfather's post, that they might still be there somewhere.

As far as reconstructing the partition table goes, the windows system partition would have been a primary, but the rest is anyone's guess. There are more than 4 partitions listed, so at least some of them must have been logical, but I think there are no conventions that might tell you which one. The various manufacturers set up there partitions as they see fit.

Apart from that, I am a bit doubtful about your chances with that approach anyway, because at least some of the drive has been written to during the Ubuntu install. As far as I know, those recovery tools work best when nothing has been written to the drive.
Good luck with it, anyway.

---

### Post by cr4321 on 2010-07-12
From what I recollect, WIN-7 in a laptop creates at least 3 partitions.

One is a small 500mb partition for the boot loader.
Another about 8 or 10 gb to create a recovery disk
and the rest big one for the main c: directory.

Kindly confirm once again .. since I am a little vague about it.....
cr4321

---

### Post by audiomick on 2010-07-12
> **cr4321 said:**
> From what I recollect, WIN-7 in a laptop creates at least 3 partitions.

One is a small 500mb partition for the boot loader.
Another about 8 or 10 gb to create a recovery disk
and the rest big one for the main c: directory.

Kindly confirm once again .. since I am a little vague about it.....
cr4321
This is right, as far as I know. There is also likely to be one with system tools from the manufacturer. For instance, my netbook has a partition on it called "Lenovo", although I don't know what is on there.

---

### Post by cr4321 on 2010-07-13
Right - that is the OEM partition where they have diagnostics, drivers and or system recovery tools.

---

