---
title: "Automount, Unmount, Remount - NTFS partitions"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by SKhan on 2010-06-11
i want to auto-mount ntfs partitions at start up. and at the same time want to be able to manually unmount and remount any of them as a user (not root).
currently ntfs partitions are auto-mounted at startup. i am also able to manually unmount any of the ntfs partitions as a non root user. The problem is only with manually remounting them.

when i try to manually remount as a non root user, it gives the following error
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160095&d=1276278741[/IMG]

my fstab file looks like this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=5071b407-9d56-4168-8ea1-09c77a84ef97	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=3C5C748E5C7444A4	/media/Others	ntfs-3g	defaults,users	0	1
#Entry for /dev/sda7 :
UUID=7ABE6B88BE6B3C2F	/media/SK	ntfs-3g	defaults,users	0	1
#Entry for /dev/sda1 :
UUID=9C58DE1C58DDF4CC	/media/Win	ntfs-3g	defaults,users	0	1
#Entry for /dev/sda6 :
UUID=A8865ED9865EA818	/media/bittorrent	ntfs-3g	defaults,users	0	1
#Entry for /dev/sda4 :
UUID=9087ec0a-c007-4462-953d-1879303b04eb	none	swap	sw	0	0

```

if technically possible, please avoid solving the problem via terminal. I now prefer to edit fstab file in order to solve the problem.

CASE HISTORY:
It was annoying to manually mount all the ntfs partitions each time after start up.
I searched a lot on google and these forums, and read a lot of threads and articles. None solved my problem.
I installed pysdm. It solved one problem but created another one, so uninstalled it. 
I installed "ntfs configuration tool".  It solved one problem but created another one, so uninstalled it too.
I also played around with fstab in the meantime.

---

