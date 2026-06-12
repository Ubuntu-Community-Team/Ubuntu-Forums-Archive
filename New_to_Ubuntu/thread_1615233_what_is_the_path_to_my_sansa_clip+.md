---
title: "what is the path to my sansa clip+?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by hanzj on 2010-11-06
what is the path to my sansa clip+?
Please help. I'm trying to install Rockbox onto it.

mount gives

> 
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
gvfs-fuse-daemon on /home/hanzj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hanzj)
/dev/sr0 on /media/PKDK00101 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)



after i unmounted the Sansa device (by right-cliking on its desktop icon and choosing "unmount"), i got this for printout of unmount:

> 
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
gvfs-fuse-daemon on /home/hanzj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hanzj)
/dev/sr0 on /media/PKDK00101 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


---

### Post by hanzj on 2010-11-06
lsusb gives:

Bus 001 Device 010: ID 0781:74d1 SanDisk Corp.

---

### Post by hanzj on 2010-11-06
when USB mode is set to MTP, the path is /home/hanzj/.gvfs


I got that info from mount printout:
> gvfs-fuse-daemon on /home/hanzj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hanzj)



but when i try USB mode of MSC, the desktop icon doesn't show up.

---

