---
title: "Just formatted but can't write to drive"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by For_the_moves on 2010-10-10
Hello all, I'm running Ubuntu 10.04 LTS and just formatted an additional hard drive in ext3 using gparted. For some reason I can't write to the drive. How do I do change this?

---

### Post by sandyd on 2010-10-10
> **For_the_moves said:**
> Hello all, I'm running Ubuntu 10.04 LTS and just formatted an additional hard drive in ext3 using gparted. For some reason I can't write to the drive. How do I do change this?
post output of
```

sudo fdisk -l
cat /etc/fstab
mount -l

```

---

### Post by For_the_moves on 2010-10-10
***sudo fdisk -l***
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005dadb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76346   613240832   83  Linux
/dev/sda2           76346       77826    11888641    5  Extended
/dev/sda5           76346       77826    11888640   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeee4c848

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   83  Linux

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020d4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       77825   625121280    f  W95 Ext'd (LBA)
/dev/sdc5               2       77825   625121248+   7  HPFS/NTFS

```

***cat /etc/fdisk***
```
cat: /etc/fdisk: No such file or directory

```


***mount -l***
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/darren/.Private on /home/darren type ecryptfs (ecryptfs_sig=4a0e3f38959192bf,ecryptfs_fnek_sig=a3566c41bc62ea1b,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/darren/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darren)
```

---

### Post by sandyd on 2010-10-11
> **For_the_moves said:**
> ***sudo fdisk -l***
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005dadb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76346   613240832   83  Linux
/dev/sda2           76346       77826    11888641    5  Extended
/dev/sda5           76346       77826    11888640   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeee4c848

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   83  Linux

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020d4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       77825   625121280    f  W95 Ext'd (LBA)
/dev/sdc5               2       77825   625121248+   7  HPFS/NTFS

```***cat /etc/fdisk***
```
cat: /etc/fdisk: No such file or directory

```***mount -l***
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/darren/.Private on /home/darren type ecryptfs (ecryptfs_sig=4a0e3f38959192bf,ecryptfs_fnek_sig=a3566c41bc62ea1b,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/darren/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darren)
```
```

sudo mkdir /media/shared
chmod 777 /media/shared
nano /etc/fstab

```plonk this onto a new line at the bottom of the file
```

/dev/sdb1 /media/shared ext3 noatime,exec,users 0 0

``````

sudo mount /dev/sdb1
```Hard disk should now mount to /media/shared and be writable. for all users.

---

### Post by For_the_moves on 2010-10-11
When I tried **mkdir /media/shared** I got:

```
mkdir: cannot create directory `/media/shared': Permission denied
```

---

### Post by sandyd on 2010-10-13
> **For_the_moves said:**
> When I tried **mkdir /media/shared** I got:

```
mkdir: cannot create directory `/media/shared': Permission denied
```
I have to admit, im very typo prone.
fixed.

---

### Post by For_the_moves on 2010-10-16
I tried **chmod 777 /media/shared** and got

```
chmod: changing permissions of `/media/shared': Operation not permitted
``` 

Any help on that?

---

