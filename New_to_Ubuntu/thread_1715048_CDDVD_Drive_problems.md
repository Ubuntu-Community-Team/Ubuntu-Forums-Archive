---
title: "CD/DVD Drive problems"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by frogknowledge on 2011-03-26
I see the CD/DVD Drive icon in the computer folder when I insert a disk the drive spins but the computer does nothing.

When I right click > Properties > Basic
Name CD/DVD Drive
Type: unknown type (application/octet-stream)
size: unknown
Location: computer:///
Volume unknown
accessed unknown
modified unknown

When I right click > Properties > Permissions
The permissions of "CD/DVD Drive" could not be determined.

**This is my MTAB file:**
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jmunk/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jmunk 0 0

**and this is my FSTAB**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d3b26f92-a8e9-47ae-9a36-0f76dabf2373 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2d584271-ccb7-4156-b604-d87f104bad89 none            swap    sw              0       0
#/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0


Pleas can anyone figure out what happen. It did work but with a recent update now it does not work anymore.

---

### Post by Dark_Stang on 2011-03-26
Quick and easy test, can you boot from the drive? The drive could be bad or the lens could just be dirty.

---

