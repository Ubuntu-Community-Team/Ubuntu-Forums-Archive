---
title: "fstab ?"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by LadyA on 2010-08-24
I'm trying to learn about fstab and from seeing examples where I've seen the CDROM listed, shouldn't my CDROM be listed under my Floppy listing? Here is my fstab.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=302fca4d-f812-4dda-b7a3-ed290415008b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=657ad981-ca9e-4774-adff-d05724a0bb01 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by CharlesA on 2010-08-24
It's fine from the looks of it.

Take a look at the page here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

