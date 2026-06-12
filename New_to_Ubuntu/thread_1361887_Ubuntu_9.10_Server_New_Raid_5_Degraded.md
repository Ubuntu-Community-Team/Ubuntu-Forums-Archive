---
title: "Ubuntu 9.10 Server New Raid 5 Degraded?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by atomictoyguy on 2009-12-22
I am a total noob to linux so I figured I would post here.

I have installed Ubuntu Server 9.10 on a homebrew server. I successfully installed the OS on a Raid 1 Array and I got the swap partition figured out. I have also been successful in getting the default desktop environment installed. What I am having trouble with is getting a raid 5 array working. 

The Raid 1 is a 40GB partition that is on an old 80GB IDE WD HD and the mirror is a 40GB partition on the first 1.5TB WD Green.

I have a total of 5 1.5TB WD Greens installed in the rig. 

Last night I setup the Raid 5 array using Palimpsest. I started the creation of the file system (ext3) and went to bed. I woke up this morning and it looked as if it had completed. I mounted the drive, and it placed an icon on the desktop for it. I double clicked it, and it opened an "explorer" window. (sorry I don't know the linux term) So I thought everything was ok.

I then rebooted the system, because I had a video driver that needed a reboot. Upon rebooting the system didn't mount the drive. So I opened up Palimpsest and went to start the Array. Upon starting the array I noticed the Status was "Degraded" and one of the drives was listed as "Spare".

I then tried the "Check" and "Repair" buttons neither of which did anything to resolve this. 

After that I stopped the array and deleted all the partitions associated with it and rebooted the machine. Once rebooted I went back into Palimpsest and tried to create a new Raid 5 array once I did this it started trying to repair the array. But still showed it as Degraded and one disk as a spare. 

So basically I am stumped. I don't know where to go from here. There is no data on this array and the only catch is that I have used part of one of the 1.5TB drives for redundancy of the operating system. I have tried searching the forums, but have yet to find the answers I need. 

Can any one out there help me figure this out?:confused:

---

### Post by lemming465 on 2009-12-24
What does *cat /proc/mdstat* have in it?  And could we also see *cat /etc/fstab* and *sudo fdisk -lu*?  We're going to need some more information before we can puzzle this out.

---

### Post by rirwin2002 on 2010-04-13
I have the same problem:

-----
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[0] sda1[3] sdc1[1]
      3907028736 blocks super 1.2 level 5, 128k chunk, algorithm 2 [3/2] [UU_]
      [===================>.]  recovery = 98.7% (1930054788/1953514368) finish=101.6min speed=3843K/sec
      bitmap: 8/466 pages [32KB], 2048KB chunk

unused devices: <none>

-----
cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=a630035f-fb08-4e93-aec2-69c3e38d4750 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=fee43577-cd72-46d4-bd81-72f6f4367001 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

-----
sudo fdisk -lu
[sudo] password for ryan: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d9f24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   716804234   358402086    7  HPFS/NTFS
/dev/sdb2       716804235   724611824     3903795   82  Linux swap / Solaris
/dev/sdb3       724611825   976768064   126078120   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  3907029167  1953514583+  ee  GPT

WARNING: The size of this disk is 4.0 TB (4000797425664 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


Disk /dev/md0: 4000.8 GB, 4000797425664 bytes
2 heads, 4 sectors/track, 976757184 cylinders, total 7814057472 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System

---

### Post by rirwin2002 on 2010-04-13
Btw, I was pleased that when I removed a disk the raid 5 array still worked.  This time it gave me an extra warning that my array was degraded. 

Overall, I think the issue is that the software utility is too sensitive. When I was using these drives not in an array, the SMART utility was giving me a warning that the disk had been used outside of normal design parameters.  Another posting suggested that this was due to the hard drives being too new.

---

