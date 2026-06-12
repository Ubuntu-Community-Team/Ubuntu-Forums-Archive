---
title: "ipod mounting issue with fstab"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by Krystallynn341 on 2011-08-25
I'm trying to mount my iPod touch 2g on Ubuntu 10.10 but the iPod won't show up in my system. 
My fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/sda1 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

my mtab:
/dev/loop0 / ext4 rw,errors=remount-ro,commit=0 0 0
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
/dev/sda1 /host fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/krystal/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=krystal 0 0


I when I put in dev/ sdc2 in my fstab the iPod will then show up. However it tells me that the dev/ sdc2 does not exist. I don't understand.
Please help.

---

### Post by Krystallynn341 on 2011-08-25
Nevermind... I just had to reboot and it worked lols

---

