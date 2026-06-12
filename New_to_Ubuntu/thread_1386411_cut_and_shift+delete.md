---
title: "cut and shift+delete"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by xieu90 on 2010-01-20
hi everyone
i heard that when someone press shift+del then the computer will only forget where the data is.(i think it delete the pointer or address of data on the hdd)
so the data is still there.

that was in window.
what about linux/ubuntu ?
when i press shift + del it say my data will be permanent deleted.
what does it mean?
will the pointer of my data deleted or will the data itself be deleted ?

and what about cut ? (from a to b)
after cutting will the data from a be deleted or only its pointer ?

---

### Post by lykwydchykyn on 2010-01-20
> **xieu90 said:**
> hi everyone
i heard that when someone press shift+del then the computer will only forget where the data is.(i think it delete the pointer or address of data on the hdd)
so the data is still there.

that was in window.
what about linux/ubuntu ?
when i press shift + del it say my data will be permanent deleted.
what does it mean?
will the pointer of my data deleted or will the data itself be deleted ?

and what about cut ? (from a to b)
after cutting will the data from a be deleted or only its pointer ?

It's the same in Linux, though as I understand it recovering the data without the pointer (the technical term in Linux is inode) is a bit more difficult due to the way the filesystems work.  There is a tool for recovering deleted files out there, I believe.

When it says "permanently deleted", it's distinguishing from the normal function of the delete key which is to put a file in the trash.


As for cutting and pasting, it depends:  if you are doing it on the same disk partition, the inode is merely updated with the new file location.  The data doesn't actually move on disk.  If you cut and paste to a different partition, the obviously the data must be moved.

But unless you actually install some kind of "secure delete" program (there are several in the repositories), your data remains on the disk to eventually be overwritten as other files are written to the file system.

---

### Post by jrothwell97 on 2010-01-20
The "pointers", as you call them, are deleted. (This isn't exactly how it works: in reality, the directory listing is deleted for it and the space is marked as free for re-use, but that isn't really important.)

There are secure delete programs in the repository, but if you are willing to use the Terminal, all you need to do to overwrite a file is to run

```
shred myfile.name
```

and then permanently "delete" it as normal (either with shift-delete or by dragging to the Trash and emptying.)

---

### Post by xieu90 on 2010-01-21
I see
thank you ^^

---

