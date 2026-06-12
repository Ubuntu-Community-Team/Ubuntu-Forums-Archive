---
title: "Help Mounting NTFS Partitions"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by danmpem on 2009-01-06
Just so nobody has to wonder, this is not a normal "how-to" on mounting ntfs on ubuntu.  I already know some of the ntfs-3g commands for the teminal.  My question is this: how can I set it up so all my other partitions will automatically mount at start up?  It's a home computer and I have some other users, so I need it to be done without them entering the root password (if possible).  The funny thing is is that when I boot from a Knoppix disc, the partitions seem to be fine, but they won't mount on Ubuntu (the error screen suggests that the partitions may be unclean).  How can I clean up the partitions?

Thanks

P.S.  If this is already in another thread, I do apologize.  I did try to find it already.

---

### Post by beattyml1 on 2009-01-06
I believe that you must edit your /etc/fstab file

```
sudo cat /etc/fstab
```

I got the following output

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=b140f677-303e-4a6b-9975-273165bab456 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1ed23ef4-6b74-4745-939d-9df91512ada2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I'm not completely sure of what all needs to be put in as far as the options go but if you need to know let me know and I'll do a little more research and see what I dig up

---

### Post by HotShotDJ on 2009-01-06
Applications --> Add/Remove... install NTFS Configuration Tool.
After it is installed, run Applications --> System Tools --> NTFS Configuration Tool.

---

### Post by beattyml1 on 2009-01-06
I forgot to mention that after you make the changes to this file you use the following command to apply them
```
sudo mount -a
```

---

### Post by JoshuaRL on 2009-01-06
beattyml1's idea, although technically correct, might be a fair amount harder than HotShotDJ's.  I'd probably suggest that for a new user.  But good effort and willingness to follow through beattyml1.

---

### Post by -kg- on 2009-01-07
> **danmpem said:**
> Just so nobody has to wonder, this is not a normal "how-to" on mounting ntfs on ubuntu.  I already know some of the ntfs-3g commands for the teminal.  My question is this: how can I set it up so all my other partitions will automatically mount at start up?  It's a home computer and I have some other users, so I need it to be done without them entering the root password (if possible).  The funny thing is is that when I boot from a Knoppix disc, the partitions seem to be fine, but they won't mount on Ubuntu (the error screen suggests that the partitions may be unclean).  How can I clean up the partitions?

Thanks

P.S.  If this is already in another thread, I do apologize.  I did try to find it already.

Yes, in order to automatically mount partitions at boot time, they must be set up to do so in your /etc/fstab file.  You can find a very good "How-To" at:

[http://ubuntuforums.org/showthread.php?t=283131&highlight=How+To+Fstab]("http://ubuntuforums.org/showthread.php?t=283131&highlight=How+To+Fstab")

---

