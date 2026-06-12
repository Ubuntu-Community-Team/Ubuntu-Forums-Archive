---
title: "Network mount"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by Crooksey on 2006-09-14
I have 2 ubuntu machines, one has a folder of 57GB of data, both computers are networked through a router, so my question is, how do i mount the 57GB of data of the network. All i am looking to do is place a folder on one desktop that contains the files of the other desktop, any ideas?

---

### Post by kidders on 2006-09-14
NFS is most probably the way to go ... unless, of course, you'd like the shares to be more widely compatible with non-Linux systems.

Just like many other filesharing protocols, you can put your NFS mountpoints in /etc/fstab too, if you'd like.

---

### Post by tbonius on 2006-09-14
Or SMB... Samba mounts are totally feasible as well.. and are a little more modular in their options.  It just depends on the type of systems and the security you wish to apply to the "shared" filesystems.

T

---

