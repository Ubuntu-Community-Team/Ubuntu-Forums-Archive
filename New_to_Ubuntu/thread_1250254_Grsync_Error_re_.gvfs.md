---
title: "Grsync Error re .gvfs"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by mapes12 on 2009-08-26
/home/mark contains a hidden file .gvfs

Grsync complains - rsync: readlink_stat("/home/mark/.gvfs") failed: Permission denied (13)

and that's running Grsync as su

1. What does .gvfs do?
2. Would it be OK to --exclude it?

---

### Post by drs305 on 2009-08-26
Here is a link explaining .gvfs:
[http://en.wikipedia.org/wiki/GVFS]("http://en.wikipedia.org/wiki/GVFS")

Yes, you should exclude .gvfs.

---

