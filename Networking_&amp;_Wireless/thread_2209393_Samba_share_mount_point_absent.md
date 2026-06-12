---
title: "Samba share mount point absent"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by UndercoverLawyer on 2014-03-05
I have a samba share mounted which is fully accessible via Dolphin in Kubuntu 12.04.3; the server is Win '03.
It mounts over a wired LAN using the following script:

*#!/bin/sh*
*dolphin smb://192.168.0.11*

I've checked in each of these places: 
[B]/home/your_user_name/.gvfs
/mnt
/media
[/B]
However, in none of these places do I see any listing of the share. I looked using bash as well as the GUI, and checked for hidden files.

Is there somewhere else it could be mounted?

---

### Post by UndercoverLawyer on 2014-03-05
Here's the output of *mount*:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

