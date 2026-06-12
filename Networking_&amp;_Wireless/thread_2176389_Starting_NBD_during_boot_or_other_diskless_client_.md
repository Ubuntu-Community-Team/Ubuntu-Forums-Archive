---
title: "Starting NBD during boot or other diskless client solution"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by Neil_Simon on 2013-09-24
How can I start an NBD client connection during the boot sequence?

I want to have a diskless client setup where the clients use overlayroot. The lower directory/filesystem will be a read-only NFS and the upper directory/filesystem will be an NBD, but I can't seem to get it to create the /dev/nbd0 device at the right time in the boot sequence.

I would prefer to have had the overlayfs on the server and NFS export it, but it seems that overlayfs does not support NFS.

---

### Post by Neil_Simon on 2013-09-24
I have since decided to go with NBD using the copy-on-write feature and completely drop NFS. It's slow but simpler to implement and that counts for a lot.

---

