---
title: "Unable to write external drive"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by jratliff on 2009-08-11
I know this has been asked and solved numerous times, but I am unable to get my external drive to mount as writeable although I have done it many times in the past.

My fstab entry is:

/dev/sdc1 /media/external vfat defaults,user,exec,uid=1000,gid=100,umask=000,utf8,shortname=mixed 0 0

The drive mounts but it is read only. I've tried

sudo chmod 700 /media/external and get:

chmod: changing permissions of `/media/external/': Read-only file system

Any help is greatly appreciated. I'm trying to use rsync (which I've done many times) to back up an internal drive, but without write permissions, it's not working.

---

### Post by colau on 2009-08-11
> **jratliff said:**
> I know this has been asked and solved numerous times, but I am unable to get my external drive to mount as writeable although I have done it many times in the past.

My fstab entry is:

/dev/sdc1 /media/external vfat defaults,user,exec,uid=1000,gid=100,umask=000,utf8,shortname=mixed 0 0

The drive mounts but it is read only. I've tried

sudo chmod 700 /media/external and get:

chmod: changing permissions of `/media/external/': Read-only file system

Any help is greatly appreciated. I'm trying to use rsync (which I've done many times) to back up an internal drive, but without write permissions, it's not working.

Can you post:
```

sudo fdisk -l
sudo cat /etc/fstab

```

---

### Post by jratliff on 2009-08-11
> **colau said:**
> Can you post:
```

sudo fdisk -l
sudo cat /etc/fstab

```

Sure:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x601c407b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        1913    15358108+   7  HPFS/NTFS
/dev/sda2               1           1        8001   df  BootIt
/dev/sda3            1914        4462    20474842+  83  Linux
/dev/sda4            4463      121601   940919017+   c  W95 FAT32 (LBA)

Partition table entries are not in disk order

Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
18 heads, 63 sectors/track, 3445352 cylinders
Units = cylinders of 1134 * 512 = 580608 bytes
Disk identifier: 0x413ed2a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     3445352  1953514552+   b  W95 FAT32

Disk /dev/sdc: 2000.3 GB, 2000398934016 bytes
15 heads, 63 sectors/track, 4134422 cylinders
Units = cylinders of 945 * 512 = 483840 bytes
Disk identifier: 0x000859ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     4134417  1953512001    b  W95 FAT32



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=7a3b2f2a-05ab-4329-a8ae-fce6a42a40f1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=9afb928a-169d-4ca7-9eee-fd70e6570b06 none            swap    sw              0       0
/dev/scd0 /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4 /media/data vfat defaults,user,exec,uid=1000,gid=100,umask=000,utf8,shortname=mixed 0 0
/dev/sdb1 /media/tunes vfat defaults,user,exec,uid=1000,gid=100,umask=000,utf8,shortname=mixed 0 
/dev/sdc1 /media/external vfat defaults,user,rw,exec,uid=1000,gid=100,umask=000,utf8,shortname=mixed 0 0
#/dev/sdc2 /media/external vfat defaults,user,exec,uid=1000,gid=100,umask=000,utf8,shortname=mixed 0 0

TIA

---

### Post by colau on 2009-08-11
Report after this.
```

sudo mkdir /media/SDC
sudo mount -t vfat /dev/sdc1 /media/SDC
cd /media/SDC
ls

```

---

### Post by jratliff on 2009-08-11
> **colau said:**
> Report after this.
```

sudo mkdir /media/SDC
sudo mount -t vfat /dev/sdc1 /media/SDC
cd /media/SDC
ls

```

Thanks for your reply colau. Dragging a file to /media/SDC in Nautilus reports

Error while copying to "SDC".
The destination is read-only.

---

### Post by colau on 2009-08-11
> **jratliff said:**
> Thanks for your reply colau. Dragging a file to /media/SDC in Nautilus reports

Error while copying to "SDC".
The destination is read-only.
Did you try this?
```

gksudo nautilus

```

---

### Post by libra1780 on 2009-08-11
generally i use /mnt for manual mounting and especially with vfat's i mount with the rw option

should be (if i remember right)
```
sudo mount -t vfat /dev/sdc1 /media/SDC -o user,auto,rw,umask=000

```

in your case

also check SDC permissions. As a folder created by root it is only writable as root. could affect your disk access too.

just to be sure
```
sudo chmod 777 /media/SDC 
```

greetz

p.s. normaly auto,user,umask=000 should do the trick

---

### Post by jratliff on 2009-08-11
Thanks guys, but unfortunately, the drive still shows up as read-only. I know it's working physically as I am able to pull files off of it.

Please keep trying with me.

Thanks.

---

### Post by amac777 on 2009-08-11
There might be corruption or errors on the drive that is causing it to be mounted read-only for safety. Try using fsck to check/fix the errors (drive must be unmounted first):

```
sudo umount /dev/sdc1
sudo fsck /dev/sdc1
```

---

### Post by jratliff on 2009-08-11
> **amac777 said:**
> There might be corruption or errors on the drive that is causing it to be mounted read-only for safety. Try using fsck to check/fix the errors (drive must be unmounted first):

```
sudo umount /dev/sdc1
sudo fsck /dev/sdc1
```

Thanks amac777. I tried this and got:

There are differences between boot sector and its backup.
Differences: (offset: original/backup)
  71:42/20, 72:41/20, 73:43/20, 74:4b/20, 75:55/20, 76:50/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 

I tried both 1) and 2) and each time got:

malloc:Cannot allocate memory

Any more help would be appreciated.

---

### Post by amac777 on 2009-08-11
Hmmm.. At least you know there is at least one error on the partition (could be more because if it weren't for fsck crashing, it might report other errors after it fixed that one)

I did a google search for "fsck malloc" and the first hit was somebody having an issue with this under vfat with the same error: [http://linux.derkeiler.com/Newsgroups/alt.os.linux/2006-05/msg00577.html](http://linux.derkeiler.com/Newsgroups/alt.os.linux/2006-05/msg00577.html)

Anyway, maybe somebody else has some ideas, but if I were in your situation, I would just make a backup copy of all the data on that drive (if you don't have this already) and then reformat the partition and start over with a clean partition.

---

### Post by jratliff on 2009-08-11
> **amac777 said:**
> if I were in your situation, I would just make a backup copy of all the data on that drive (if you don't have this already) and then reformat the partition and start over with a clean partition.

Thanks very much. This is actually what I have already done and this is the second time I have run into this. I was hoping to avoid doing it again as there is about 1.5Tb of data on the internal drive and it takes more than 20 hours over an eSata connection to do this backup. I don't have a compelling reason to use FAT other than the off chance I'll need to use this backup with someone else's Windows machine. Do you think the problems are FAT-related and I should just format it ext3?

---

### Post by amac777 on 2009-08-12
I'd guess the problems are FAT related but that's a total guess. The follow-up to the person having the same problem in the web link I posted earlier suggests the other person to use ext2 because Windows can read that filetype via a program. I'm pretty sure I've read ext3 in windows too so perhaps you could check out ext2/3 compatability in windows. Assuming it's good enough for your purposes, that would probably be a more stable file system for lots of data.

---

