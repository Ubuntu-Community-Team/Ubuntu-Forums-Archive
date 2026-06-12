---
title: "Sharing  NTFS drives with NFS"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by nobull on 2007-09-27
I have been having problems sharing my NTFS server(6.10) hard drives using NFS.  They are both mounted on the server using ntfs-3g and work fine.  When I try to mount the volume from a client(7.04) a permission denied error is returned from the server.  After practically reading every related forum on the internet, I have came to the conclusion that FUSE does not support NFS file sharing on the mainstream versions.  I have downloaded the source for FUSE and tried to compile it using a ---enable-kernel-module command but I can not get it to work.  I don't know if I am compiling correctly or not(I have never done it before), but after completing a long list of command it errors out with

***Cannot determine the version of the linux kernel source.  Please
***prepare the kernel before running this script

Does anybody know of a FUSE package that is already compiled that I can download or any other ideas?  Let me know if you need any additional information.

---

### Post by nobull on 2007-11-01
I just took the not so easy route and changed my server drives to an EXT3 format and it works good.  So never mind.

---

