---
title: "unknown contents of hdd"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-13
unknown contents of hdd


Hi,

I formatted an external hdd and seemed to have successfully transferred many files to it. However it's icon doesn't show up on my desktop now. and Gparted claims the thing is "Unallocated". Is that certain there's nothing on there?


nnjond@nnjond-desktop:~$ mount
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
gvfs-fuse-daemon on /home/nnjond/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nnjond)
nnjond@nnjond-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea053

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60239   483864576   83  Linux
/dev/sda2           60239       60802     4519937    5  Extended
/dev/sda5           60239       60802     4519936   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e67e

   Device Boot      Start         End      Blocks   Id  System
nnjond@nnjond-desktop:~$ 


Thanks.

---

