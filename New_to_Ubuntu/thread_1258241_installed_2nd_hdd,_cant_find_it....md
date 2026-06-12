---
title: "installed 2nd hdd, cant find it..."
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Darkoblivion2 on 2009-09-04
ok heres the scenario, i have ubuntu installed on one hdd, and now i have plugged in a second hard drive, how do i have my computer find the second so i can format it in gparted?

thanx in advance!

---

### Post by k33bz on 2009-09-04
go to your command line and
```
fdisk -l
```
and post here

---

### Post by NoaHall on 2009-09-04
Can you do "cat /etc/mtab" and "cat /etc/fstab", then post the output here.

---

### Post by Darkoblivion2 on 2009-09-04
> **NoaHall said:**
> Can you do "cat /etc/mtab" and "cat /etc/fstab", then post the output here.
mtab:
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-15-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

fstab:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=479ba464-d5a0-4e63-8376-5388bd996df0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=906eb9a8-c9a0-46cc-ad93-748dbecdbce8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

gvfs-fuse-daemon /home/shujin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=shujin 0 0

---

### Post by NoaHall on 2009-09-04
Hm... Can you see it through your BIOS? You might have to scan your computer for it to be detected. All this will be under your BIOS

---

### Post by Darkoblivion2 on 2009-09-04
how do i know if it is found in bios? what will it say and where?

---

### Post by NoaHall on 2009-09-04
When you start up, go into the BIOS, and somewhere under "Hard drives", it will be there.

---

