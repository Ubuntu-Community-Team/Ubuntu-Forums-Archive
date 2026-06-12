---
title: "What is a fuseblk file system?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-15
Whenever I mount my NTFS-formatted hard drive in Linux, it always mounts successfully with the file system "fuseblk".
Even if I try to manually mount at the command-line with "-t ntfs" it still reports the system as being "fuseblk".

What is this file system? Is it something akin to ntfs?

---

### Post by drs305 on 2009-03-15
Ther short answer is that "fuseblk" is just how an ntfs partition is reported via the "mount" command, among others. The "fuse" part comes from FUSE (file system in userspace).

Here is a link to the wiki on FUSE, but it probably won't give you a great deal of understanding of how FUSE works.
[http://en.wikipedia.org/wiki/Filesystem_in_Userspace]("http://en.wikipedia.org/wiki/Filesystem_in_Userspace")

An internet search of "FUSE" and "linux" would probably return something of an explanation if you are really interested.

---

### Post by Volt9000 on 2009-03-15
Great, thanks!

---

