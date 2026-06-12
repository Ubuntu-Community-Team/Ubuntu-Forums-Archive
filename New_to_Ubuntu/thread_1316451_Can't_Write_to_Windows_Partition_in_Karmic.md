---
title: "Can't Write to Windows Partition in Karmic"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by pierce_g on 2009-11-06
I recently upgraded from Jaunty to Karmic, and now I cannot write to my Windows partition. Whenever I try to copy files, I get the error: "Error while copying to "[folder name]". The destination is read-only."

I've tried copying files by doing "sudo nautilus" but I receive the same error.

Any help would be greatly appreciated. Thanks.

---

### Post by SunnyRabbiera on 2009-11-06
Actually I would not try to add new files to a dual booted windows, as sometimes adding files into it screws things up.

---

### Post by Hazey on 2009-11-06
Hi,

can you post your /etc/fstab file?

Hazey

---

### Post by pierce_g on 2009-11-06
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda5 during installation
UUID=046da21b-7a5a-4a95-8257-e2e95a2ca531  /              ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda6 during installation
UUID=b4210170-1ec9-4436-a16f-b487f7639646  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda3                                  /media/sda3    ntfs         nls=iso8859-1,ro,umask=000  0  0  
```

---

### Post by kansasnoob on 2009-11-06
Works OK here with "ntfsprogs" installed. It's in the repos.

---

### Post by Hazey on 2009-11-06
Hi,

change the options in your ntfs column from ro (read-only) to rw (read-write) and have a next try. Maybe, it's useful to add the option "user" to this column.

For more details, maybe this site can help you.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Hazey

---

### Post by pierce_g on 2009-11-06
Thank you! It doesn't get much simpler than that. :D

---

