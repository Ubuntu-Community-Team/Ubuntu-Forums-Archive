---
title: "frustrating RAID and mount issues!!"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Archer Troy on 2009-12-29
Hey guys,

This problem is completely driving me up a wall.

I recently upgraded my mythbuntu computer.

I have 3 hard drives: heres my device.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

sda is 1.5tb
sdb is 1 tb
sdc is 1 tb

All are SATA

here is my fdisk 
```
roman@roman-htpc:~$ sudo fdisk -l
[sudo] password for roman: 

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27929e80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460      182401  1453416615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584      182401  1452420553+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f14f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f14f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

```


which looks fine. 

here is my blkid:
```
roman@roman-htpc:~$ sudo blkid
/dev/sda1: UUID="01e51a52-dd53-4ca6-a858-770f74233a45" TYPE="ext3" 
/dev/sda5: UUID="05eb887e-8347-4109-8f2e-a85a2cc4851c" TYPE="swap" 
/dev/sda6: UUID="2c63dab7-a06d-4caa-8951-5eff6c71d49a" TYPE="xfs" 
/dev/sdb: TYPE="nvidia_raid_member" 
/dev/sdc: TYPE="nvidia_raid_member" 
/dev/mapper/nvidia_bbcbfebb1: UUID="bf4da045-141b-4b4e-a7ba-662a777c4852" TYPE="ext4" 
roman@roman-htpc:~$ 

```

sdb and sdc are supposedly part of the /dev/mapper/nvidia_bbcbfebb1 RAID (i guess) - which i didnt implement (mythbuntu did this automatically when i upgraded....WTF!) 	](*,)

anyways - now whenever i try to mount sdb and sdc i get:

```
roman@roman-htpc:~$ sudo mount /dev/sdb1 /mnt/sdb
mount: special device /dev/sdb1 does not exist

```

so...then i try to mount /dev/mapper/nvidia_bbcbfebb1 to sdb:

```
roman@roman-htpc:~$ sudo mount /dev/mapper/nvidia_bbcbfebb1 /mnt/sdb
roman@roman-htpc:~$ 

```

it works, EXCEPT it only mounts 1 of my 2 hard disks (sdc) that is supposedly part of the RAID  /dev/mapper/nvidia_bbcbfebb1. 

so now I have my main disk (sda) which is mounted perfectly

then i have one of my two hard disks (sdc) (not sdb) mounted through the /dev/mapper/nvidia_bbcbfebb1. 

I would be happy with either getting rid of the raid altogether and just mounting each of my drives separately (sda - /mnt/sda, sdb-/mnt/sdb, sdc- /mnt/sdc) OR just have the second hard drive included in the RAID whenever I mount it (sda - /mnt/sda , sdb and sdc -> /dev/mapper/nvidia_bbcbfebb1 -> /mnt/sdb

I'm trying to be as detailed as possible, so i hope all of this makes
sence.

ANY help would be sooo appreciated. I have absolutely no idea what to do at this point. 	](*,)	](*,)	](*,)	](*,)

Thanks everyone.

---

### Post by b0b138 on 2009-12-29
The best I can tell everything is mounting correctly. Why do you think sdb is not mounting?  Just to clarify, /dev/mapper/nvidia_bbcbfebb1 is what's created by raid. So instead of mounting /dev/sdb1 or /dev/sdc1 separately, you mount /dev/mapper/nvidia_bbcbfebb1 to a mount point (/mnt/name_of_mountpoint)

---

### Post by Archer Troy on 2009-12-29
So i messed around with the hardware and think i figured out a bit more info...still don't know how to fix the problem though.

basically I think its mirroring the drives.

SDA - is my boot drive and is mounting properly

SDB and SDC are both 1tb hard drives. Raid 1 is mirroring the drives into 1 drive under the /dev/mapper/nvidia_bbcbfebb1.

does anyone know how to remove RAID 1 (mirroring) so that both drives will be seen as seperate drives (sdb and sdc).

if its a matter of formatting, that wouldn't be a problem.

RAID is disabled in BIOS.

---

### Post by b0b138 on 2009-12-29
What is the output of ```
sudo dmraid -r
```

---

### Post by Archer Troy on 2009-12-30
```
roman@roman-htpc:~$ sudo dmraid -r
[sudo] password for roman: 
/dev/sdc: nvidia, "nvidia_bbcbfebb", mirror, ok, 1953525166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_bbcbfebb", mirror, ok, 1953525166 sectors, data@ 0
roman@roman-htpc:~$
```

---

### Post by b0b138 on 2009-12-30
First, triple check that raid is turned off in bios.

Then run ```
sudo dmraid -rE
``` This should remove the metadata from the drives

Then post the output of the first command again

---

### Post by Archer Troy on 2009-12-30
Wow. you rule man.

that definitely fixed it.

everything is completely back to normal.

Thank you so much.

I really really appreciate it.

---

