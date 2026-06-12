---
title: "Second Hard-Drive"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by UnrealClock on 2010-08-19
I have two hard-drives at the moment, and only one of them is listed by linux. I'm not dual-booting anything, and there isn't anything on the second hard-drive. How to I go about formatting it to for daily linux use?

---

### Post by halitech on 2010-08-19
first off, is the second drive seen by your systems BIOS? If it is, does the drive have anything on it now?

post the output of
```
sudo fdisk -l
```
and
```
sudo mount
```

---

### Post by UnrealClock on 2010-08-19
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097053

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112412672   83  Linux
/dev/sda2           13995       14594     4805633    5  Extended
/dev/sda5           13995       14594     4805632   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7ca49d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14592   117210208+   7  HPFS/NTFS

```

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
gvfs-fuse-daemon on /home/unrealclock/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=unrealclock)

```

The computer knows it's there, I just want to be able to access it.

---

### Post by halitech on 2010-08-19
ok, Ubuntu is seeing it as well

```
/dev/sdb1               1       14592   117210208+   7  HPFS/NTFS
```
now, you have 2 options. You can leave it formatted as NTFS or you can use Gparted to reformat the drive to ext3/4 

After you make that decision, you need to add the drive into to fstab

```
gksudo gedit /etc/fstab
```

I'm not good on using the UUID like Ubuntu wants to use so hopefully someone else can give you info on setting that up

---

### Post by john newbuntu on 2010-08-20
It appears to me that you might have an older version of Ubuntu. The modern ones automatically detect and indicate this in the Places menu. See if this helps:
[https://help.ubuntu.com/community/MountingWindowsPartitions#Automatic%20Configuration](https://help.ubuntu.com/community/MountingWindowsPartitions#Automatic%20Configuration)

---

