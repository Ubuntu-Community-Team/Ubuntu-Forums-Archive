---
title: "[SOLVED] Auto-Mount XP Partition"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Chrissd on 2009-01-03
Hi, just installed Ubuntu onto my wife's laptop, but she wanted to keep Windows XP 'just incase'. She wants to be able to access her files from the XP partition, which I know can be done. I've had problems doing this myself, wondering if anyone can help, as we're both PC newbs. :(

I've asked a similar question before, so I'll be predictive and tell you the outputs of various commands:

sudo fdisk -l
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8abb8ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4803    18097222+  83  Linux
/dev/sda3            4804        4864      489982+  82  Linux swap / Solaris

```

sudo blkid
```

/dev/sda1: UUID="120C3A5A0C3A38D5" TYPE="ntfs" 
/dev/sda2: UUID="dd72559b-60d8-456d-9937-f31ffe79e3ef" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="b79735f2-d62b-447c-bdce-3be6b940bbb0" 

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dd72559b-60d8-456d-9937-f31ffe79e3ef /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=b79735f2-d62b-447c-bdce-3be6b940bbb0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

mount
```

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/melissa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=melissa)

```

Thanks very much in advance :)

---

### Post by taurus on 2009-01-03
Use ntfs-config to configure that ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Chrissd on 2009-01-03
Thanks, what would an example of what I might want the mount point to be? :)

---

### Post by taurus on 2009-01-03
Perhaps you could use /media/windows as the mount point for your ntfs partition.  Then, there would be an icon on the desktop so she just has to click the icon to access that partition.

---

### Post by Chrissd on 2009-01-03
That's perfect, exactly what we wanted, we both thank you so much for your help! :D

---

