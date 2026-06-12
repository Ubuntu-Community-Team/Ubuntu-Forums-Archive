---
title: "how do updates to ext4 work?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by PGScooter on 2009-07-07
Hi,

From what I understand, updating ext4 means updating the kernel, right? What about all the files that have already been written in ext4? Are they kept in the old format, the new format, or are they the same format?


thanks

---

### Post by Sef on 2009-07-07
> PGScooter

From what I understand, updating ext4 means updating the kernel, right? What about all the files that have already been written in ext4? Are they kept in the old format, the new format, or are they the same format?
The file system itself - ext4 - was added to the kernel.   So was ext3.   The files that are in ext4 will not be hurt by an update to ex4, just like ext3.  [Sticky on ext3 and ext4]("http://ubuntuforums.org/showthread.php?t=1133719").

---

