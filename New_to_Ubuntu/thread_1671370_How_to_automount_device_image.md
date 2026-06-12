---
title: "How to automount device image?"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by victorhugo289 on 2011-01-19
Hi guys, what would I have to modify here to automount a 51MB ext3 filesystem image I made myself using "dd if=/dev/zero..." and "mkfs.ext2":

------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/home/car/r/I.iso    /home/car/r/I    udf,iso9660 user, loop    0 0
/home/car/r/II.iso    /home/car/r/II    udf,iso9660 user, loop    0 0
-------------------------------------------------------------------------

Mine would be like:

/home/user/Desktop/miniHDD.img   /media/miniHDD    ???, ????, ??, ??

I copied that from another post on how to mount ISO images at startup, but mine is not an ISO image, it's ".img", and it's Ext3.

Any help would be appreciated. Thanks.

Victor

---

### Post by yetiman64 on 2011-01-20
I'll include a portion of my fstab file to demonstrate automounting (I do it as "read only" so as not to corrupt the original backup file) the image files of 2 partitions, "/ and /home", of this very install.

```
# Loopmount backup images at startup (read only):
/media/Linux-strg1/a_SYSTEM-BACKUPS/LUCID_64/Install-180111/Root/L64Rt_180111.img    /media/automount1    ext4    loop,ro        0    0
/media/Linux-strg1/a_SYSTEM-BACKUPS/LUCID_64/Install-180111/Home/L64Hm_180111.img    /media/automount2    ext4    loop,ro        0    0
```I am defining my partitions as ext4 (same as the original partition), you'd need to put ext3. Also besides the loop option I put the option "ro" so both my backups are kept as read only.

This is a precaution and am unsure if it is necessary but prefer to play it safe with my system backups.

/media/automount1 and /media/automount2 are folders I created manually with,
```
sudo mkdir /media/<foldername>
```,before attempting to mount.

You can always test if a mount setup is correct with
```
sudo mount -a
```, if any faults are present they will show in the terminal output.

To manually unount a folder use
```
sudo umount /path/to/mount-folder
``` eg /path/to/mountfolder would be /media/automount1 or /media/automount2 in my case.

Note, I've never tried to write to a backup file mounted like this, but if your image is not critical you could try changing the "ro" option to "rw" and test it out.

---

### Post by victorhugo289 on 2011-01-20
Excellent, worked perfectly!

---

