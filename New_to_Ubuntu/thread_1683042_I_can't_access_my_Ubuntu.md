---
title: "I can't access my Ubuntu"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by bzyk3 on 2011-02-06
On my 250GB HD I   put Ubuntu 10.04, Kubuntu 10.04 and Win.XP.  Last few months  I used
only Ubuntu without  any problems.  Yesterday  the partition become unaccessible.
  Using Life CD I try mount   it but I received the error  : 
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda6, 
       missing codepage or helper program, or other error 
       In some cases useful info is found in syslog - try 
       dmesg | tail  or so

The picture of my HD:

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 251.1 GB, 251059544064 bytes 
255 heads, 63 sectors/track, 30522 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x03545c30 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        8792    70621350+   7  HPFS/NTFS 
/dev/sda2            8793       30523   174553089    f  W95 Ext'd (LBA) 
/dev/sda5           16124       23772    61440561    e  W95 FAT16 (LBA) 
/dev/sda6            8793       15818    56434688   83  Linux 
/dev/sda7           15818       16123     2449408   82  Linux swap / Solaris 
/dev/sda8           23773       30242    51963904   83  Linux 
/dev/sda9           30242       30523     2260992   82  Linux swap / Solaris 

Partition table entries are not in disk order 

   Kubuntu and Win.XP works very well . The GRUB has change. The  texts for Ubuntu are gon.
 How can I recover my data what I have in this operating system ?
I'm not very good with Linux but  I like it. Please help me strait up my computer.

---

### Post by 123456789123456789123456 on 2011-02-06
use terminal
log in to kubuntu
you know the folder that the ubuntu system is located at?
search for it in kubunt, should be under /dev/
find the partition
use sudo ls -l on that partition, for instance "sudo ls -l /dev/disk1
that should show all information on it.
try also from that sudo command to open the disk partition.
if it allows you, which from what I read, it should, since sudo gives you root access to the drive.  find the information you want to back up.  use the sudo cp -r command to copy all the files to a folder on the kubuntu installation.  reformat and install ubuntu again over the previous installation, and copy back over the files, from kubuntu, using the sudo cp -r command

search for cp command on the internet, it should give you the syntax on how to use it, -r stands for recursive.  bassicly it will copy every file, and subfolder, inside a certian folder/location to another.

---

### Post by bzyk3 on 2011-02-08
Ubuntu is installed  on  /dev/sda6 but I can't mount and open this partition.  I try live CD Knoppix
and Ubuntu 10.10.     Could you tell me how  look  the commends   in the terminal ?
   
The  attachment show  my  HD  in  KdiskFree  under Knoppix.

---

### Post by M0use on 2011-02-08
Looks like you have a corrupted partition
try 
sudo fsck /dev/sda6
from the terminal

---

