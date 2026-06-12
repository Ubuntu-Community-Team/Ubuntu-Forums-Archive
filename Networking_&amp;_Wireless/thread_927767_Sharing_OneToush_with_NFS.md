---
title: "Sharing OneToush with NFS"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Azyx on 2008-09-23
Hi.
I have one Ubuntu 8.04 as a fileserver and share some disk under NFS. I bought a new 750GB USB-drive and put in


# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/100GB_F  10.1.1.0/255.255.255.0(rw)
/media/280GB_C  10.1.1.0/255.255.255.0(rw)
/media/280GB_D  10.1.1.0/255.255.255.0(rw)
/media/280GB_E  10.1.1.0/255.255.255.0(rw)
/media/OneTouch4 10.1.1.0/255.255.255.0(rw)

I added the last line and restart with:

sudo /etc/init.d/nfs-kernel-server restart

I get a warning:

exportfs: Warning: /media/OneTouch4 does not support NFS export.

Is It not possible to share NTFS-disks or USB trough NFS? (I forgot to format the disk to ext3, befor I beguinne to fill the disk)

/Azyx

---

