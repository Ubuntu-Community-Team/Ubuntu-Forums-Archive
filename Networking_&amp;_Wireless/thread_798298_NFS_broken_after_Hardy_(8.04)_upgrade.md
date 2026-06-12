---
title: "NFS broken? after Hardy (8.04) upgrade"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by aussiedaddy on 2008-05-18
Have just installed Hardy (8.04) on two PCs - 1 running 64 bit.

I can't get them to connect to my NFS server (7.10 server edition) although they seem to be configured correctly (and the same as PCs running 7.10 which connect fine).

I can see the server mounts from the 8.04 PCs - by that I mean they are reported correctly by 

showmount -e <name_of_my_NFS_server>

But when I type

sudo mount <mount_point>

I get:

mount.nfs4: No such device

I may be doing something wrong but I can't see it.  All my 7.10 PCs mount the share happily.

Is anyone out their having the same problem?  Is there any change to the way NFS clients hve to be set up with hardy?

Thanks for reading my post.

---

### Post by aussiedaddy on 2008-05-18
Both PCs now accessing NFS server.

64 bit machine after I did:

sudo apt-get remove nfs-common
sudo apt-get install nfs-common

The 32 bit machine after another software update which mandated a restart.

---

