---
title: "External DVD no longer found"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by htrufan on 2010-09-15
My external DVD rom is no longer detected after my asus eee battery died while in the middle of getting files from the drive.  It was working fine before the low-battery-forced shutdown.  I am new to Ubuntu.  I have tried a few things from similar posts but no dice.

This is my fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation

Here is lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

mount gives:
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
gvfs-fuse-daemon on /home/xxxxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxxxx)


Thanks

---

### Post by CharlesA on 2010-09-15
What kind of external dvd drive is it, USB, firewire?

Dvd drives won't show up in blkid or fdisk, since they are not fixed disks.

Try unplugging it and booting into Ubuntu, then plugging it back in once it's up and running.

---

### Post by htrufan on 2010-09-16
Hmm,  I swear I tried rebooting unplugged and then plugging back in already and that didn't work.  But this time is has.  Did you mean unplugging the power on the DVD drive as well?  I didn't do that last time, but did this time.  Anyway, thanks.

---

