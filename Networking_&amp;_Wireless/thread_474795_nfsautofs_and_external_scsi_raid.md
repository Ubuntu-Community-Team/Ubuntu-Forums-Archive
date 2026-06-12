---
title: "nfs/autofs and external scsi raid"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by disasm on 2007-06-15
I got an mpt scsi raid unit (external) hooked up to an ubuntu workstation. It works fine, is exported over NFS, and autofs is used to mount it from the other workstations. The computer also has a second hard drive that's exported over NFS. When I access the second hard drive over nfs everything is fine, when I access the raid unit over nfs, I get I/O timeout errors. I first suspected a problem with the raid unit, but when I locally access the raid unit I don't get any errors.

Here is what I get when I try to tar -tvf a file:
Cannot read: Input/output error
tar: Too many errors, quitting

Then if I try ls, or retry untarring that file I get:
Permission denied

I'm at a loss as to what could be the problem, any ideas anyone?

Sam

---

