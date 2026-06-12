---
title: "Western Digital 2TB not mounting"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by SGStriker on 2010-09-25
Hello, im not a first time user for Ubuntu but nether am i an expert. my WD 2TB external hard drive is being detected but will not mount so i cannot view or use anything store on my hard drive... when i got in to my storage devices window and try to manually mount i get this as an error in these details.

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed
 
if someone can give me some help id be greatly appreciative. i really hope this is a none format kinda fix...... ><"

---

### Post by SGStriker on 2010-09-25
let me make a quick amendment.... my WD was formated when i got it and i turned it into a FAT system using ubuntu 10.10 beta as the operating system...  thought that might help a bit

---

### Post by Darkness Des on 2010-09-25
You're running Ubuntu off of a FAT partition? Bad idea, man... But anyways, it says that it's already mounted as your root partition. Meaning you're running the system off of that thing you're trying to mount.

---

### Post by SGStriker on 2010-09-25
no... my external is running on FAT my internal hard drive ext 4 as standard with most formats with ubuntu it seems when i installed it... (my other FAT hardrive a 500 gb is fat and works just fine.....)

---

### Post by papibe on 2010-09-26
Could you tell us the result of:
```
$ mount -l
$ sudo fdisk -l
```
before and after you connect the disk?

---

### Post by SGStriker on 2010-09-26
> **papibe said:**
> Could you tell us the result of:
```
$ mount -l
$ sudo fdisk -l
```
before and after you connect the disk?

For the first command line i get:
```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sgangelstriker/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sgangelstriker)

```

then:

```
[sudo] password for sgangelstriker: 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008dba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18732   150456320   83  Linux
/dev/sdb2           18732       19458     5831681    5  Extended
/dev/sdb5           18732       19458     5831680   82  Linux swap / Solaris

Disk /dev/sda: 1999.7 GB, 1999696297984 bytes
255 heads, 63 sectors/track, 243115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a4e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243116  1952827392    7  HPFS/NTFS

```

---

### Post by jamessimo on 2010-09-26
Can Disk Utility pick it up? System > Administration > Disk Utility.

---

### Post by SGStriker on 2010-09-26
Yes it can. when i said storage devices widow i meant disk utility.... sorry but the answer is yes.... it does everything but mount.....

---

### Post by papibe on 2010-09-26
It appears that your 2TB external HD is /dev/sda1 (not sdb1), so try to mount it on Disk Utility or (assuming you have a /media dir):

```
$ sudo mount /dev/sda1 /media
```
Regards.

---

### Post by JustinR on 2010-09-26
Hi,

Disk Utility (Palimpsest) will also report error.

Your MTAB file is incorrectly configured.
You can change it manually, by changing your '/' partition to it's actual device name.
(Eg. My Ubuntu install had the same problem with the external drive, my Ubuntu install was at '/dev/sdb' but reported as '/dev/sdc' in MTAB, and my external drive tried mounting on '/dev/sdc' - which confused Disk Utility.

So go into disk utility, and find your Ubuntu partition's actual device (eg. /dev/sdb), Press ALT + F2 and type 'gksudo gedit', open up /etc/mtab, and change your root partition to the device from Disk Utility.

Example: Disk Utility displayed my Ubuntu partition as /dev/sdb although MTAB displayed it as /dev/sdc. This was obviously an error that messed up my mounting of external HDDs. 
```

/dev/sdc1 / ext4 rw,errors=remount-ro 0 0

```
I had to change mine:
```

/dev/sdb1 / ext4 rw,errors=remount-ro 0 0

```

Restart your computer, and everything should be working.

---

### Post by SGStriker on 2010-09-26
thank you so much... i restarted a while back and it seemed to fix it .... but i used JustinR's trick and i believe i wont encounter this problem again.... thank you all~~~!

---

