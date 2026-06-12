---
title: "sshfs not working on Hardy"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by manoj_paul_joseph on 2008-07-03
sshfs fails on Hardy with the following error message.

manoj@mowgli:~$ sshfs root@rhel5:/ws /mnt/rhel5
sshfs: relocation error: sshfs: symbol fuse_opt_insert_arg, version FUSE_2.6 not defined in file libfuse.so.2 with link time reference

Looks like an incompatible version of libfuse.so. Is this a known issue?

This is my configuration.

manoj@mowgli:~$ apt-cache show fuse-utils | grep Version
Version: 2.7.2-1ubuntu2
manoj@mowgli:~$ apt-cache show sshfs | grep Version
Version: 1.9-1
manoj@mowgli:~$ uname -a
Linux mowgli 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

Anybody knows what I could do to fix this?

---

### Post by manoj_paul_joseph on 2008-07-03
Compiling my own sshfs (sshfs-fuse-2.0 from [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)) did the trick. I am now able to use sshfs.

-Manoj

---

