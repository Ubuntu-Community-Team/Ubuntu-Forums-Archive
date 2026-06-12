---
title: "NFS: exporting CD Drive"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by apollo2011 on 2008-03-21
I have a MacBook Pro with Leopard that I use primarily along with my Ubuntu 7.10 desktop. I share most of the files on my Linux desktop with the Mac over NFS. One of the disadvantages of the desktop is that I only have one cd drive, so I would like to share one or both of the cd drives in the desktop, preferably over NFS, since I have that in place already.

However, when I add /media/cdrom0 to the /etc/exports/ file, restarting NFS gives the following error:

> exportfs: Warning: /media/cdrom0 does not support NFS export.

I don't see why NFS should have any problem exporting the directory (especially when there is a disc inserted and mounted to that directory. I can't find any information on Google that explains how to mount a cdrom drive in NFS. Below are my /etc/exports and /etc/fstab files.

> # /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/ksut/ *(rw,insecure,no_subtree_check,async,all_squash,anongid=1000,anonuid=1000)
/media/Home/ksut/ *(rw,insecure,no_subtree_check,async,all_squash,anongid=1000,anonuid=1000)
/media/Data/ *(rw,insecure,no_subtree_check,async,all_squash,anongid=1000,anonuid=1000)
/ *(ro,insecure,no_subtree_check,async,all_squash,anongid=1000,anonuid=1000)

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=a6c5965a-919b-488e-9de5-1054df7d7893 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb4
UUID=91aac5a4-2215-4b7b-b73b-72a4feeb2d56 /media/Home     ext3    defaults        0       2
# /dev/sdb3
UUID=e7826428-eaf0-459b-86ac-253a2a694440 /media/Data     ext3    defaults        0       2
# /dev/sda2
UUID=066C20B86C20A501 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=3e6558e7-b6dd-4c39-b5c2-03b545a61410 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Any help is greatly appreciated. Thanks!

---

