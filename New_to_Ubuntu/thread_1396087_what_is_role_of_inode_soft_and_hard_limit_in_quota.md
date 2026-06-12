---
title: "what is role of inode soft and hard limit in quota file?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by legolas_w on 2010-02-01
Hi
Can someone please let me know what is the role of inodes soft and hard limit in the quota definition file?

When we can limit the number of blocks, why we need to also limit the inodes?

Thanks

---

### Post by legolas_w on 2010-02-02
Hi,

Any comment?

Thanks

---

### Post by legolas_w on 2010-02-03
Any comment?

Thanks.

---

### Post by legolas_w on 2010-02-05
hi,

Any comment?

Thanks

---

### Post by mikechant on 2010-02-05
> Can someone please let me know what is the role of inodes soft and hard limit in the quota definition file?

When we can limit the number of blocks, why we need to also limit the inodes?

When a filesystem is set up the maximum number of inodes (roughly speaking the maximum number of files) is fixed.
If you created lots of tiny files, you could fill up the inode table before you ran out of space, and probably cause the system to crash when a critical process was unable to create a file. So either space or inodes can run out first and you need to limit each seperately.

The soft limit can be exceeded temporarily (for up to a week by default, from what I've read). The hard limit cannot be exceeded at any time.

---

### Post by legolas_w on 2010-02-10
So the inode number specifies the files number meaning that we have one and only one inode per file. Right?

---

### Post by mikechant on 2010-02-11
> So the inode number specifies the files number meaning that we have one and only one inode per file. Right? 

The inode number is essentially an arbitary but unique number. It provides the means of mapping a directory entry to a physical file, and a way of referencing an open file (even if its directory entry has been deleted).

In other words, a directory entry contains a filename and an inode number. 
The inode itself contains the device name and disk address of the actual file. 

There is one inode per file, and one file per inode, but multiple directory entries can point to the same file.

See this for further details:
[http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)

---

