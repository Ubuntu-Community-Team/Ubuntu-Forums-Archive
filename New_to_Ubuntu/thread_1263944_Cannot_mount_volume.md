---
title: "Cannot mount volume"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Silver! on 2009-09-11
Hi. I'm having a problem, can't mount any of my hard drive partitions..

> ricardo@Ricardo-Coelho:~$ cat /etc/mtab
/dev/sdb6 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-14-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdb7 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ricardo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ricardo 0 0
ricardo@Ricardo-Coelho:~$ sudo fdisk -l
[sudo] password for ricardo: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ea81ea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19456   115322602+   f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686    7  HPFS/NTFS
/dev/sda6           10199       19456    74364853+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x129b129a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244192504+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           30402       34341    31648050    f  W95 Ext'd (LBA)
/dev/sdb3           34342       60802   212541336    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb5           30402       30680     2241036   82  Linux swap / Solaris
/dev/sdb6           30681       31896     9767488+  83  Linux
/dev/sdb7           31897       34341    19639431   83  Linux


Dunno if any of that is helpful, but I saw it in another thread..

Hopefully someone can help me, usually the partitions are mountable, but sometimes, I dunno why, it doesn't work and it's really annoying.

EDIT: Ok, I believe it was because I turned off windows incorrectly, but that's just the thing, I can't turn off windows, since it's been acting up and won't shut down, just says "Windows is shutting down.".
Is there any way I can go around "turning it off correctly"?

EDIT2: Managed to enter windows safe mode, rebooted, mounting fine now!

---

### Post by mapes12 on 2009-09-12
sdb does look as if the partitions have been set up correctly. 

> Partition 1 does not end on cylinder boundary.
Partition 3 does not end on cylinder boundary.

means that something has gone wrong with the space where the partition is installed.

Also,

> /dev/sdb5 30402 30680 2241036 82 Linux swap / Solaris
/dev/sdb6 30681 31896 9767488+ 83 Linux
/dev/sdb7 31897 34341 19639431 83 Linux 

the swap partition should be at the end, not the begining of the Ubu configuration.

This will explain more: [http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning](http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning)

and the main page is here: [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by talsemgeest on 2009-09-12
Try: ```
mkdir ~/sda1
sudo mount -t ntfs /dev/sda1 ~/sda1
```

---

### Post by Bucky Ball on 2009-09-12
This is solved already? See edit #2 in original post.

---

### Post by talsemgeest on 2009-09-12
> **Bucky Ball said:**
> This is solved already? See edit #2 in original post.
Heh, I need to read these things better...

---

