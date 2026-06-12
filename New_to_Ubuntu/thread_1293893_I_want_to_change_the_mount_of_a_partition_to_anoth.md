---
title: "I want to change the mount of a partition to anothe location"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by knowledgestudent on 2009-10-17
Hi all, 
when I installed ubuntu I have formatted 50 GB to be ext3 and to mount to /usr/local, now when I open usr/local I find folders , but I can not neither create new folder nor paste, so that I thought to mount the  parition to another location so that I changed in the /etc/fstab file and changes the folder to another directory, now it is muonted two directories, 

what I wanted from alla of that; is I needed the 50 G, to be just for my personal data files in the ubuntu , but now I can not even create a sub directory, ????:confused:

any suggestions, 
thanks in advance

---

### Post by rbc on 2009-10-17
/usr/local is probably owned by root, hence you not being able to write to it. Type this in terminal:
sudo fdisk –l (that last character is a lower case L)
Post back with the results, and also provide your /etc/fstab file

---

### Post by ajgreeny on 2009-10-17
You probably simply need to change the ownership of the current mount point folder to your username ```
sudo chown username:username /usr/local/mountfolder
```This assumes all the files are yours already, but if not you may need the command to be recursive ```
sudo chown -R username:username /usr/local/mountfolder
```

---

### Post by knowledgestudent on 2009-10-19
> **rbc said:**
> /usr/local is probably owned by root, hence you not being able to write to it. Type this in terminal:
sudo fdisk –l (that last character is a lower case L)
Post back with the results, and also provide your /etc/fstab file

thanks for fast reply,and sorry for being late,
here is the fdisk-l command result: 
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a3cfdca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sda2            9729       38913   234428512+   f  W95 Ext'd (LBA)
/dev/sda5            9729       19456    78140128+   7  HPFS/NTFS
/dev/sda6           19457       31006    92775343+  83  Linux
/dev/sda7           31007       37803    54596871   83  Linux
/dev/sda8           37804       38913     8916043+  82  Linux swap / Solaris
```

and here is the fstab file content : 
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=5fcf3231-65dd-4e55-887b-bbd6e2ea5330 /               ext3    relatime,errors=remount-ro 0       1
# /usr/local was on /dev/sda7 during installation
UUID=e0f69d10-0306-4cc4-abd1-50b8f844558d /storage      ext3    relatime        0       2
# swap was on /dev/sda8 during installation
UUID=64cb0da5-19fd-4a3f-978d-17ec63f870c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I have tried to use the Gparted , but I got only the option "unmount" is activated but when I try to use, it gives me msg that the device is busy !!!!!

suggestions please!!!!
Regards,

---

### Post by knowledgestudent on 2009-10-19
> **ajgreeny said:**
> You probably simply need to change the ownership of the current mount point folder to your username ```
sudo chown username:username /usr/local/mountfolder
```This assumes all the files are yours already, but if not you may need the command to be recursive ```
sudo chown -R username:username /usr/local/mountfolder
```

Hi thanks for replying, 
I have tried the first command, and now I can create new folder and paste what ever I need, thanks a lot , 

on addition I wonder if there is a way to enlarge the partition that the ubuntu already installed on !!!, i.e can add some Gigas to the ubuntu partition??? 


Regards,

---

### Post by rbc on 2009-10-19
Glad to see that ajgreeny’s suggestion help. As far as enlarging the partition….You are going to need a LiveCD e.g. Ubuntu LiveCD or GParted LiveCD. You won’t be able to grow the Ubuntu partition while it is mounted and being used. I cannot remember if GParted comes “pre-installed” with the Ubuntu LiveCD, but you can always download it. Personally, I have always had better luck with GParted Live, as the GParted that comes with Ubuntu Live seems to automatically mount the swap partition, and I cannot for the life of me convince swap to unmount

---

### Post by ZankerH on 2009-10-19
For the record, the "correct" (default) location where users have their "personal" space is the /home/user folder, so if you want your stuff on a separate partition, mount it on /home. Your best bet is probably to make a "/usr/local/you" folder, and delegate its ownership to yourself, however all your settings will still be stored in the "real" home folder.

---

### Post by ancientnoob on 2009-10-24
Finally moved  from a wubi installation in XP to sda2 on the same hard disk, using LVPM which reported a successful migration. Although GRUB now offers the option of booting to the new location the keypress automatically transfers to the old XP line and I'm back via wubi.
Is there a simple way to insist that GRUB goes to the sda2 mount point?

The forums have been very helpful in the struggle to harness various devices (turntable, webcam, printer, virtualbox, wine et al) and the successes led to my running out of space on the wubi root.disk.  However I hope that I don't have to start from scratch with a fresh installation.

The partition editor shows that there is indeed a linux sda2 partition although there doesn't seem to be any provision for a swap disk. Could this be a legacy of the wubi arrangement which presubably used its windows host directory in the original install?

The following data also suggests that the migration actually took place and this is borne out by observation of sda2 when mounted:

user@ubuntu:~$ sudo blkid
[sudo] password for user: 
/dev/loop0: UUID="5eb1cb52-125e-4101-9eea-a13b7ccf58e5" TYPE="ext3" 
/dev/sda1: UUID="8E947CD1947CBD71" TYPE="ntfs" 
/dev/sda2: UUID="3095ab86-6a65-422f-b7e3-384189435478" SEC_TYPE="ext2" TYPE="ext3" 

Apologies if I've entered this forum inappropriately.

---

