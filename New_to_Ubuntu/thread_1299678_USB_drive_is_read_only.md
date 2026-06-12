---
title: "USB drive is read only"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2009-10-24
I have a USB drive that auto mounts but only as read-only. It was used in Windows briefly and my guess is that I removed it without properly unmounting it from Windows and there is probably some corruption. This has happened to me before, and I would go back into Windows and repair or reformat it.

The problem I have now is that I don't have access to any Windows OS. Is there any way to do this from Linux only? I have tried chown command, gparted doesn't work as it only lets me wipe what it sees and that does not include the small portion on it that is formatted in NTFS. Hell, I even tried qtparted which didn't do much of anything.

---

### Post by carnagex420x on 2009-10-24
```
cat /etc/fstab
```

make sure the options don't say "ro", should be "defaults"

Is is formated in NTFS or FAT32?

---

### Post by Bigtime_Scrub on 2009-10-24
Sorry I should have included my fstab in the first post. Well it was formated in ntfs. I used gparted to wipe it clear, it is unallocated space now. I right-click-format from the desktop and when I try to set it to fat32 it says it is read only.
```
 cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Sun Oct  4 01:21:17 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=ae19d261-1178-4d6c-aa86-a12f2432a772 /boot                   ext3    defaults        1 2
/dev/mapper/VolGroup-lv_root /                       ext4    defaults        1 1
/dev/mapper/VolGroup-lv_swap swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
none /sys/bus/usb/drivers usbfs devgid=503,devmode=664 0 0

```

---

### Post by carnagex420x on 2009-10-24
Try to format it manually.

```
umount /dev/sd*
mkfs.vfat /dev/sd*
```

or possibly mount as rw manually

```
mount /dev/sd* -o rw
```

---

### Post by NESFreak on 2009-10-24
nevermind, you already removed the partition. You should go to gparted again and create a new partition. Which should then automatically be formatted to the filesystem you've chosen in gparted to create.

---

### Post by nothingspecial on 2009-10-24
Sorry, ignore that. I thought it was formatted ntfs, but then I reread your last post.

---

