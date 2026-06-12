---
title: "mounting fat32 drive"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by MeanStreak on 2009-06-07
Hi,

I have two hard drives in my PC - I'm trying to mount the fat 32 partition (/dev/sdb2) - could someone please advise how I can do this?

Cheers

---

### Post by gfk on 2009-06-07
Well I only know how to make the mount perminent.  Which involves editing the fstab file.  If your interested then follow these intrutions.

First you must find out the UUID for the partition.
Copy this in a terminal.
```
ls /dev/disk/by-uuid -lah
```
Find the one for sdb2.  You will need this information later.

Then you need to create a folder for the partition.  Most people put it in /media/

Then open up the fstab file.  You'll need root permission for this.  Copy this in a terminal.
```
sudo gedit /etc/fstab
```
Somthing like this should come up on your editer.
```
# /etc/fstab: static file system information.
#
# <file system> 			  <mount point>   <type>  <options>       <dump>  <pass>
proc            			  /proc           proc    defaults        0       0
# /dev/sdb8
UUID=d2a3f178-ce47-4107-841e-289cb09a2a40 /               jfs     relatime,errors=remount-ro   0       1
# /dev/sdb6
UUID=f21d0595-77b0-4775-95aa-f03abc16b932 /boot           ext3    noatime,nodiratime,data=journal,commit=600   0    2
# /dev/sdb5
UUID=b08c28b3-327d-4742-be6c-569fe001e34f /home           jfs     relatime        0       2
# /dev/sdb7
UUID=2a74c6fb-794c-474b-a248-396cfb22c93d /var            jfs     relatime        0       2
# /dev/sda1
UUID=F8F48DC4F48D861A /media/sda1-Documents  ntfs-3g  noatime,nodiratime,auto,exec,nouser,rw,umask=002,gid=46,utf8   0  1
# /dev/sda2
UUID=64A0E067A0E04162 /media/sda2-Videos     ntfs-3g  noatime,nodiratime,auto,noexec,nouser,rw,umask=002,gid=46,utf8   0  1
# /dev/sda3
UUID=480E-A4E7 /media/sda3-FAT32-Pagefile    vfat     noatime,nodiratime,noauto,noexec,nouser,ro,utf8,umask=007   0  1
# /dev/sda5
UUID=47E2-4F85 /media/sda5-FAT32             vfat     noatime,nodiratime,auto,exec,nouser,rw,umask=000,gid=46,utf8   0   0
# /dev/sda6
UUID=082a30fa-ad16-4145-a099-8d4e55835507    none         swap    sw              0       0
/dev/scd0				  /media/dvdrom	  udf,iso9660   user,noauto,exec,utf8   0       0

```
So you need to add the information about the partition.

You see I have a fat32 partition mount at /media/sda5-fat32.
Just copy that it you want and replace my information with yours.
Like you would need to replace my UUID with what you got and change the mount point info with what you chosen.

If you want more info then in a terminal type ```
man fstab
```.  It's very detailed.

Also here's a link for another quick guide.  [HTML]http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Mounting_FAT32_Partitions[/HTML]

---

### Post by Mornedhel on 2009-06-07
It looks like your drive works and is recognized already. The simplest solution may be to go in the Places menu and check if it's listed somewhere under "Computer" ; if it is, just click the entry.

If it's not, follow the previous poster's advice (fstab, mount, and others).

---

