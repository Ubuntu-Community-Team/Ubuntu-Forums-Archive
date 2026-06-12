---
title: "[SOLVED] Problems with CHMOD"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by fairy._.queen on 2009-01-07
Hello! I'm a newbie and this is my first post :-)
I have a problem with my data-HDD: it's regolarly mounted, but only the superuser can write on it.
If I try to change permission with chmod, e.g. as in
```
sudo chmod -R 777 /media/sda4
```
it does say it's changed everything, but in fact it's not.
If I look at the disk properties with dolphin he keeps showing me the group has not writing privileges.
Can you please help? Thanks in advance!

---

### Post by Titan8990 on 2009-01-07
What format is the drive?

---

### Post by Simian Man on 2009-01-07
As Titan8990 said, the file system the drive uses is important.  In particular FAT has no notion of permissions.  I reformatted my thumb drive as ext2 to avoid this problem.

---

### Post by fairy._.queen on 2009-01-07
It's a FAT32 (I put "vfat" in fstab).
Incredibly I'm having no problem with the NTFS partition instead [sigh]

---

### Post by fairy._.queen on 2009-01-07
Thanks both of you for your reply!
I dont understand this: you say fat has no permission, but the "ls -l" command output for that folder is:
```
drwxr-xr-x 4 root root 16384 1970-01-01 01:00 sda4
```

which shows, if im correct, that root has rwx privileges, the group rx etc.
What do you mean?

P.s.: I need that hdd to be accessed by both kubuntu and windows and I was told fat was the best file system for that. do you disagree?

---

### Post by Michael.Godawski on 2009-01-07
hi, 
and what happens if you do this:

make new mount point

```
sudo mkdir /media/windowsfat
```

mount the partition
```

sudo mount /dev/sda4 /media/windowsfat -t vfat -o umask=000
```

can you please post also the output of 

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Drubie on 2009-01-07
> **fairy._.queen said:**
> 
P.s.: I need that hdd to be accessed by both kubuntu and windows and I was told fat was the best file system for that. do you disagree?

fat should work well then, as windows has no idea what to do with ext2.

> **fairy._.queen said:**
> 
```
drwxr-xr-x 4 root root 16384 1970-01-01 01:00 sda4
```

which shows, if im correct, that root has rwx privileges, the group rx etc.


yes, and since you are sudo-ing, I dont see what the problem could be...
I would try again and reformat unless you have something you need on the drive

---

### Post by fairy._.queen on 2009-01-07
> **Michael.Godawski said:**
> 

can you please post also the output of 

```
sudo fdisk -l
cat /etc/fstab
```

This is the new output of "ls -l":
```
lrwxrwxrwx 1 root root     6 2009-01-07 01:23 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2009-01-07 01:23 cdrom0
drwxr-xr-x 3 root root 16384 1970-01-01 01:00 sda1
drwxrwxrwx 1 root root  4096 2009-01-07 17:37 sda2
drwxr-xr-x 4 root root 16384 1970-01-01 01:00 sda4
drwxr-xr-x 4 root root 16384 1970-01-01 01:00 windowsfat

```

This is the output of "fdisk -l"
```
Disco /dev/sda: 40.0 GB, 40007761920 byte
255 testine, 63 settori/tracce, 4864 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x70000000

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        1538    12289725    7  HPFS/NTFS
/dev/sda3            1539        2747     9711292+   5  Esteso
/dev/sda4            2748        4864    17004802+   b  W95 FAT32
/dev/sda5            1539        2558     8193118+  83  Linux
/dev/sda6            2559        2747     1518111   82  Linux swap / Solaris

```

this is the output of "cat /etc/fstab":
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7dfe4279-1cdd-4886-a146-188c99098c34 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=38b7488b-504d-4d87-911b-cf353b605fd1 none            swap    sw              0       0
/dev/sda1       /media/sda1     msdos           defaults,users  0       0
/dev/sda2       /media/sda2     ntfs-3g         users,dev,auto,exec,suid,async,rw       0       0
/dev/sda4       /media/sda4     vfat            users,dev,auto,exec,suid,async,rw       0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Thanks both for the fast reply!

---

### Post by fairy._.queen on 2009-01-07
> **Drubie said:**
> fat should work well then, as windows has no idea what to do with ext2.



yes, and since you are sudo-ing, I dont see what the problem could be...
I would try again and reformat unless you have something you need on the drive

I had already reformat... :-(
thanks anyway!

---

### Post by Guruprasad on 2009-01-07
What I see is your sd4 folder is still having 755 permision.

First unmount the partition using > umount -a, then use sudo chmod command, then remount the partition and see.

---

### Post by Guruprasad on 2009-01-07
What I see is your sd4 folder is still having 755 permision.

First unmount the partition using > umount -a, then use sudo chmod command, then remount the partition and see.

---

### Post by wizard10000 on 2009-01-07
> **Simian Man said:**
> In particular FAT has no notion of permissions. 

dingdingdingdingding!  We have a winner  :)

root owns the drive because root mounted it - since FAT filesystems don't allow individual file or folder permissions.

---

### Post by mister_pink on 2009-01-07
FAT has no notion of permissions, so they are set partition wide when it is mounted. By default this means root owns it, which is a problem. You can change this in fstab

In the line that reads:

```

/dev/sda4       /media/sda4     vfat            users,dev,auto,exec,suid,async,rw       0       0

```
You can set the owner, group and permissions with by using uid=xxx,gid=xxx,umask=xxx
where xxx is the id of the owner/group you want and permissions you want. For example:
```

/dev/sda4       /media/sda4     vfat            users,dev,auto,exec,suid,async,rw,gid=46,uid=1000,umask=027       0       0

```

Edit: I should add that I don't think you need some of those other options unless you know what they're doing. I'd just go with:
```

/dev/sda4       /media/sda4     vfat            defaults,gid=46,uid=1000,umask=027       0       0

```

---

### Post by theozzlives on 2009-01-07
> **fairy._.queen said:**
> Hello! I'm a newbie and this is my first post :-)
I have a problem with my data-HDD: it's regolarly mounted, but only the superuser can write on it.
If I try to change permission with chmod, e.g. as in
```
sudo chmod -R 777 /media/sda4
```
it does say it's changed everything, but in fact it's not.
If I look at the disk properties with dolphin he keeps showing me the group has not writing privileges.
Can you please help? Thanks in advance!

```
sudo chown username /media/sda4
```

---

### Post by egalvan on 2009-01-07
> **Drubie said:**
> fat should work well then, as windows has no idea what to do with ext2.


Yes, but Linux Operators know to use "Ext2 Installable File System For Windows"

[http://www.fs-driver.org/](http://www.fs-driver.org/)


It's not perfect, but it works well.

---

### Post by fairy._.queen on 2009-01-07
It works!!!!!
Thanks guys, all of you, you're wonderful!!!
:KS

---

