---
title: "&lt;Power outage&gt;"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by dre3 on 2010-07-28
Had a brief power outage and now i can't log on my dual boot (win xp) ubuntu.  I get this 

Gnu-Grub version 1.98-1ubuntu 5

Minimal BASH-like line editing is supported.  For the first word, TAB lists possible comand completions.  Anywhere else TAB lists possible device or file comletions.

grub>


My window loads fine, thanks for any help thank u.

---

### Post by Ozymandias_117 on 2010-07-28
Boot to a live cd, mount your hard drive and run ```
fsck -a /dev/sdb2
``` (Assuming sdb2 is your hard drive and Linux partition). If you're not sure how to tell, mount your drive and post the output of ```
mount
```

---

### Post by dre3 on 2010-07-29
Ok here it is i how this is it.          aufs on / type aufs (rw) none on /proc type proc (rw,noexec,nosuid,nodev) none on /sys type sysfs (rw,noexec,nosuid,nodev) none on /dev type devtmpfs (rw,mode=0755) none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) /dev/sr0 on /cdrom type iso9660 (ro,noatime) /dev/loop0 on /rofs type squashfs (ro,noatime) none on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) none on /dev/shm type tmpfs (rw,nosuid,nodev) tmpfs on /tmp type tmpfs (rw,nosuid,nodev) none on /var/run type tmpfs (rw,nosuid,mode=0755) none on /var/lock type tmpfs (rw,noexec,nosuid,nodev) none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

---

### Post by dre3 on 2010-07-30
I'm real new to this so i don't if i did what was ask for the last thread, i know, didn't look right but if someone can tell me what to do next i would be Thankful.  Thank you.

---

### Post by cheapie on 2010-07-30
> **dre3 said:**
> Had a brief power outage and now i can't log on my dual boot (win xp) ubuntu.  I get this 

Gnu-Grub version 1.98-1ubuntu 5

Minimal BASH-like line editing is supported.  For the first word, TAB lists possible comand completions.  Anywhere else TAB lists possible device or file comletions.

grub>


My window loads fine, thanks for any help thank u.

Try typing (at that prompt):

```
insmod normal
```

then

```
normal
```

and see if you get a menu.

---

### Post by dre3 on 2010-07-30
U meant at the (grub>) prompt?  If so i type insmod normal and then normal and nothing happen.  Was i suppose to put in the live Cd?

---

### Post by sandyd on 2010-07-30
please post the output of
```

sudo fdisk -l
```
from a livecd

---

### Post by dre3 on 2010-07-30
Disk /dev/sda: 40.0 GB, 40000000000 bytes 255 heads, 63 sectors/track, 4863 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x9dc96e9e  Device Boot      Start         End      Blocks   Id  System /dev/sda1               1           5       40131   de  Dell Utility /dev/sda2   *           6        4862    39013852+   7  HPFS/NTFS

---

### Post by sandyd on 2010-07-30
> **dre3 said:**
> Disk /dev/sda: 40.0 GB, 40000000000 bytes 255 heads, 63 sectors/track, 4863 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x9dc96e9e  Device Boot      Start         End      Blocks   Id  System /dev/sda1               1           5       40131   de  Dell Utility /dev/sda2   *           6        4862    39013852+   7  HPFS/NTFS
I hate to tell you this, but the power outage seems to have made the ubuntu partiton vanish.
```
Disk /dev/sda: 40.0 GB, 40000000000 bytes 255 heads, 63 sectors/track, 4863 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x9dc96e9e 
Device Boot Start End Blocks Id System 
[B]/dev/sda1 1 5 40131 de Dell Utility 
/dev/sda2 * 6 4862 39013852+ 7 HPFS/NTFS[/B]
```

---

### Post by dre3 on 2010-07-30
Man i'm learning this to slow i wish what all that means, but that fine i just install it so i didn't lose anything so i'll just install it again, thanks to everyone that help.

---

### Post by sandyd on 2010-07-30
> **dre3 said:**
> Man i'm learning this to slow i wish what all that means, but that fine i just install it so i didn't lose anything so i'll just install it again, thanks to everyone that help.
NOTE: as a warning. you **may** have a corrupted partiton table, which will account for the missing linux partition.

double check for corruption before anything else.

---

### Post by dre3 on 2010-07-31
Kool i would like to figure this out so what   should i do next?

---

### Post by dre3 on 2010-07-31
> **carlee said:**
> NOTE: as a warning. you **may** have a corrupted partiton table, which will account for the missing linux partition.

double check for corruption before anything else.

  What do i have to do to check for corrupted partiton?

---

### Post by dre3 on 2010-08-01
I'm sure eager to get on this and fix this issue so if any of u good people can help i will be so thankful.   Ok i got my desktop up and running with the live cd i just need someone to point me in the right direction now!  Thanks>

---

### Post by dre3 on 2010-08-01
Ok i got my desktop up and running with the live cd i just need someone to point me in the right direction now! Thanks>

---

