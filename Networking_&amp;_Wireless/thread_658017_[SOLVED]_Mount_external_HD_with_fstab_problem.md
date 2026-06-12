---
title: "[SOLVED] Mount external HD with fstab problem"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by koetjeboeh on 2008-01-04
Hi all,

Having a problem with mounting a share with fstab. Searched the forum, found some post, but nothing seems appropriate.
At boot I try to mount an external hard disk that is connected to a NAS-router and set it up according to this link:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read)

fstab:

//192.168.1.1/xxx  /media/storage/  smbfs  fmask=777,dmask=777,credentials=/xx/.smbcredentials  0  0

After boot I see:

$ ls -lart /media

total 16
**?---------  ? ?    ?       ?                ? /media/storage**
drwxr-xr-x  2 root root 4096 2007-10-25 01:11 floppy0
lrwxrwxrwx  1 root root    7 2007-10-25 01:11 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-10-25 01:11 cdrom0
lrwxrwxrwx  1 root root    6 2007-10-25 01:11 cdrom -> cdrom0
drwxr-xr-x  5 root root 4096 2007-11-07 09:59 .
drwxr-xr-x 20 root root 4096 2007-12-26 17:51 ..

Manual mount:

$ sudo mount -a

Could not resolve mount point /media/storage/

The only way to mount this disk is do the following:

$ sudo umount /media/storage

$ sudo mount -a
timeout connecting to 192.168.1.1:445

$ ls -lart /media

total 20
drwxr-xr-x  2 root root 4096 2007-10-25 01:11 floppy0
lrwxrwxrwx  1 root root    7 2007-10-25 01:11 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-10-25 01:11 cdrom0
lrwxrwxrwx  1 root root    6 2007-10-25 01:11 cdrom -> cdrom0
drwxr-xr-x  5 root root 4096 2007-11-07 09:59 .
drwxr-xr-x 20 root root 4096 2007-12-26 17:51 ..
**drwxrwxrwx  1 root root 4096 2008-01-03 16:25 storage**

So fstab ssems all rigth to me. Is it possible that the timeout error with the manual mount is a problem with the execution of fstab? I see some related post is these fora and laucnhpad, but they all seem to be somewhat different or not solved.

Regards,
Fabio

---

### Post by jw5801 on 2008-01-04
The problem is most likely that fstab is mounting filesystems before networking is up and running during the boot process. I'm not sure how one would go about fixing this though...

---

### Post by koetjeboeh on 2008-01-08
> **jw5801 said:**
> The problem is most likely that fstab is mounting filesystems before networking is up and running during the boot process. I'm not sure how one would go about fixing this though...

This seems a bit odd regarding the link to ubuntuguide.org. However, I've created a simple script in cron.daily(which executes x minutes after boot with anacron).
Still, it is a bit annoying that the reason for fstab not working is not sure. I'll try to look for an answer, post back if I found one.

Regards,
Fabio

---

