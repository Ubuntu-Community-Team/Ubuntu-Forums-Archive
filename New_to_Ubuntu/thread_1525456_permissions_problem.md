---
title: "permissions problem?"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by hellomoto on 2010-07-06
when I boot up sometimes (randomly) I think I am having a problem with permissions?

My sound does not work
I am unable to mount my hard disk
I am unable to shutdown my PC unless i use "sudo shutdown -P now"

This is random and does not happen all the time, any suggestions?

2 screen shots u can see that I am unable to mount my hard disk and the lack of option to shutdown in the menu.

and in the last screen shot u can see my "hd2" and shutdown option in the menu.

---

### Post by jtarin on 2010-07-06
Post your /etc/fstab

---

### Post by hellomoto on 2010-07-06
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=1286fe16-a825-4126-896f-6672ea51febc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=b7a3d080-db42-4135-be68-024a698abf0f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3	/media/hd1 	ext4 rw,user,auto,exec    0        2

```

---

### Post by jtarin on 2010-07-06
Now post results of ```
df -T
```

---

