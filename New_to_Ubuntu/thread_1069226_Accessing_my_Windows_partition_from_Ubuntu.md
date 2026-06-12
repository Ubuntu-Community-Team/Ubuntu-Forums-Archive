---
title: "Accessing my Windows partition from Ubuntu"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Bloaergh on 2009-02-13
Evening Ubuntu forums, FNG here.  Ive been a windows user my entire life and Im just now trying to leave the cult.

Ive got Intrepid ibex dual booted on my laptop here with Windows Vista.  Im trying to access the windows partition from within Ubuntu.  Im fairly sure that i'm almost there- Google has been my mentor so far.

The last issue i'm having is actually mounting the volume.  When I use:
sudo mount /media/Windows

I get an error in the terminal, reading:
fuse: mount failed: Device or resource busy.

Does anyone know what could be causing this?  I feel so very close, and yet so far away :(

---

### Post by N4zgu1 on 2009-02-13
Cant you mount from the GUI??

---

### Post by Bloaergh on 2009-02-13
> **N4zgu1 said:**
> Cant you mount from the GUI??

Forgive me...  GUI?  Graphical user Interface?  just guessing.  Im a windows fellow, remember?:(
I'd be thrilled if you could enlighten me.

---

### Post by Captain_tux on 2009-02-13
Yes... Graphical User Interface.

To mount from the GUI: Click on **Places**, then right click and choose **mount** to mount the Windows drive. 

Welcome to Ubuntu!

---

### Post by HavocXphere on 2009-02-14
I've found that the GUI mounts don't work correctly if there was a failed attempt to auto-mount the partition in the fstab.

Anyway, I auto-mounted everything with write access like so:
(Those are all NTFS formated partitions, if you've got fat32 then you'll need to change those). Even works fine for USB external Hdds (e.g. The FreeAgent drive).

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


#Warning: The /dev/sdb5 designation can change. Use UUID...those don't change as easily

proc	/proc	proc	defaults	0	0

#Linux Main
#Entry for /dev/sda5 :
UUID=0699219e-8d53-4445-9e29-2d1d6091aeca	/	ext3	relatime,errors=remount-ro	0	1

#Linux Swap
#Entry for /dev/sda6 :
UUID=93d2953b-8fc9-4b57-8666-6f0949d99986	none	swap	sw	0	0

#DVD ROM
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

#Old OS Disk_K NTFS
#Entry for /dev/sda1 :
UUID=06D8DCA8D8DC9771	/media/DiskK	ntfs	defaults,user,exec,uid=1000,gid=100,umask=000 0 0

#Data drive (E)
#Entry for /dev/sdc1 :
UUID=D4A8A63BA8A61C4C /media/Data	ntfs	defaults,user,exec,uid=1000,gid=100,umask=000 0 0

#Programs drive (D)
#Entry for /dev/sdb5 :
UUID=6AE4D4E2E4D4B215 /media/Programs	ntfs	defaults,user,exec,uid=1000,gid=100,umask=000 0 0

#Vista OS drive (C)
#Entry for /dev/sda1 :
UUID=C400DDB700DDB122 /media/Vista	ntfs	defaults,user,exec,uid=1000,gid=100,umask=000 0 0

#FreeAgent
UUID=EE3091BD30918D69 /media/FreeAgent	ntfs	defaults,user,exec,uid=1000,gid=100,umask=000 0 0


#---------------------------------------------------------------------------------------------------
#Some comments to help sorting out which uuid is what


#Havoc@Sphere:~$ ls -l /dev/disk/by-uuid
#total 0
#lrwxrwxrwx 1 root root 10 2009-01-28 13:53 0699219e-8d53-4445-9e29-2d1d6091aeca -> ../../sdc5
#lrwxrwxrwx 1 root root 10 2009-01-28 13:53 06D8DCA8D8DC9771 -> ../../sda1
#lrwxrwxrwx 1 root root 10 2009-01-28 13:53 6AE4D4E2E4D4B215 -> ../../sda5
#lrwxrwxrwx 1 root root 10 2009-01-28 13:53 93d2953b-8fc9-4b57-8666-6f0949d99986 -> ../../sdc6
#lrwxrwxrwx 1 root root 10 2009-01-28 13:53 C400DDB700DDB122 -> ../../sdc1
#lrwxrwxrwx 1 root root 10 2009-01-28 13:53 D4A8A63BA8A61C4C -> ../../sdb1
#lrwxrwxrwx 1 root root 10 2009-01-28 11:53 EE3091BD30918D69 -> ../../sdd1


#Havoc@Sphere:~$ sudo fdisk -l

#Disk /dev/sda: 80.0 GB, 80026361856 bytes
#255 heads, 63 sectors/track, 9729 cylinders
#Units = cylinders of 16065 * 512 = 8225280 bytes
#Disk identifier: 0x9f09bb38

#   Device Boot      Start         End      Blocks   Id  System
#/dev/sda1   *           1        5222    41943040    7  HPFS/NTFS
#/dev/sda2            5223        9729    36202477+   5  Extended
#/dev/sda5            5223        9538    34668238+  83  Linux
#/dev/sda6            9539        9729     1534176   82  Linux swap / Solaris

#Disk /dev/sdb: 250.0 GB, 250059350016 bytes
#255 heads, 63 sectors/track, 30401 cylinders
#Units = cylinders of 16065 * 512 = 8225280 bytes
#Disk identifier: 0xae46ec12

#   Device Boot      Start         End      Blocks   Id  System
#/dev/sdb1   *           1        3275    26304512    7  HPFS/NTFS
#/dev/sdb2            3276       30400   217881562+   5  Extended
#/dev/sdb5            3316       30400   217560231    7  HPFS/NTFS

#Disk /dev/sdc: 160.0 GB, 160041885696 bytes
#255 heads, 63 sectors/track, 19457 cylinders
#Units = cylinders of 16065 * 512 = 8225280 bytes
#Disk identifier: 0xf1c28d09

#   Device Boot      Start         End      Blocks   Id  System
#/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

#Disk /dev/sdd: 320.0 GB, 320072933376 bytes
#255 heads, 63 sectors/track, 38913 cylinders
#Units = cylinders of 16065 * 512 = 8225280 bytes
#Disk identifier: 0xa4b57300

#   Device Boot      Start         End      Blocks   Id  System
#/dev/sdd1               1       38913   312568641    7  HPFS/NTFS


And finally, if the NTFS system wasn't shut down properly the last time then the mounts will fail. The easiest way to fix that is to boot Vista (might take longer than normal) again and do a clean shutdown.

---

### Post by bikodog on 2009-02-14
I have had success by installing ntfs-config from synaptic package manager.

Also, the bit about shutting down windows properly is most often the culprit. I would try that first.

---

