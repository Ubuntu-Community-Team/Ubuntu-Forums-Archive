---
title: "NFS share not mounted on boot"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by lemmy999 on 2008-10-04
I have set up a small network with a main server and two laptop clients. When I reboot the laptop it doesn't find or mount the share on the server.This is my /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=7a31bf8f-5ac8-4b8a-9b4f-bb53b7c10739 /               reiserfs notail          0       1
# /dev/hda4
UUID=0d7481ff-f4c3-4bf0-ad1d-aec8de45d9de /home           reiserfs defaults        0       2
# /dev/hda3
UUID=5f4ddf80-f0fc-4900-8212-02fff77431f9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
alpha:/home home/chris/shared nfs rsize=8192,wsize=8192,timeo=14,intr

---

