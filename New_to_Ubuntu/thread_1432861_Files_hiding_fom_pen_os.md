---
title: "Files hiding fom pen os"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by nnjond on 2010-03-18
Hi,

I've installed 9.10 on a pen drive while leaving existing files on the pen  intact. However i don't seem to be able to find them from the pen os. Is it possible to access them?

Thanks

---

### Post by Paqman on 2010-03-18
Are you sure they're still there? Unless you created a separate partition the whole drive will have been formatted when you installed.

---

### Post by nnjond on 2010-03-18
Found them cdrom

Thanks

---

### Post by Doctor Mike on 2010-03-18
> **nnjond said:**
> Hi,

I've installed 9.10 on a pen drive while leaving existing files on the pen  intact. However i don't seem to be able to find them from the pen os. Is it possible to access them?

ThanksAssuming when you installed and ran the partition manager you did not wipe the original partition it may be listed under places (top of desktop) just under computer.

If its not listed check under system-administration-system monitor and click file systems tab. If the file system is recognized by Ubuntu it should be listed there.

If the file system is not recognized you'll need to identify its file type (like NTFS) and look for a tool to get Ubuntu to recognize it.

---

