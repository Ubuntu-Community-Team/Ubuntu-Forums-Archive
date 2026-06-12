---
title: "NFS server/client"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by nwadams on 2007-12-12
so i can mount certain files but not others
my /etc/exports file has the line
/media/320 192.168.0.117(rw)

and then i go: sudo exportfs -a and i get
nwadams@nwadams-desktop:~$ sudo exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.117:/media/320".
Assuming default behaviour ('no_subtree_check').
NOTE: this default has changed since nfs-utils version 1.0.x
exportfs: Warning: /media/320 does not support NFS export.


now i can mount my home partition, but i can't mount this one, would it have something to do with how it says it is owned by root?

Thanks

---

