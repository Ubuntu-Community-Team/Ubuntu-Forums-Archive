---
title: "Mount Windows Partition on Startup"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by prismpirate on 2009-03-05
Listed below is my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8b566284-6390-4bd3-9bf1-b35d9e7ae9bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b57e6831-5aaf-4745-85d8-9d6f6b2dd1ba /home           ext3    relatime        0       2
# /dev/sda5
UUID=44a3baba-c267-4985-8ad3-f8b55aeadc0f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

The current situation I face is that I have to mount my partition once per startup, instead of having it mount automatically. I currently run Ubuntu 8.10. Any suggestions as to how I might mount it on startup

---

### Post by theozzlives on 2009-03-05
Try this:
[http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")

---

### Post by prismpirate on 2009-03-05
> **theozzlives said:**
> Try this:
[http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")
How do I find out the number of the NTFS partition?

---

### Post by taurus on 2009-03-05
Look at the output of this command from a terminal to find out which partition is ntfs.

```
sudo fdisk -l
```

---

