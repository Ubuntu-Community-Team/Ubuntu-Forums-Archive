---
title: "How do you set drive permissions?"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by falsepod on 2011-01-20
I'm using Ubuntu 10.10 on a Packard Bell Dot S Netbook. I have an external USB drive thats formatted with the Apple File Storage. I have write permission on OSX but when I connect it to my Linux machine I only get read access.

I know how to write in the command line, but I don't have any understanding on what I'm doing, i've just followed online tutorials to help fix problems I've had. I can't find one that tells me how to set drive permissions though. I assume probably because its really easy to do. If you can help, please break things down for me, I'm a complete newbie.

---

### Post by Layvian on 2011-01-20
Can I get a little bit more information, what is one the drive(Don't need names just media types.).  I run Ubuntu on my Macbook, and I had the same issue, even if you set it for everyone to read & write , you can not access the data.  I assume it has something to do with OS X and Encryptions from tampering rather then a simple command-line or check mark.

---

### Post by mikewhatever on 2011-01-20
Be aware:

[http://en.wikipedia.org/wiki/HFS_Plus](http://en.wikipedia.org/wiki/HFS_Plus)
> The Linux kernel includes the hfsplus module[10] for mounting HFS+ filesystems. HFS+ fsck and mkfs have been ported to Linux and are part of the hfsprogs package.[11]

The Linux HFS+ kernel driver has support to read and write to HFS+ non-journaled drives/parititions **but only has read support of journaled HFS+.** Journaling ability got added to HFSplus when OSX came out and is by default on for OS X installations. Journaling is a redundant behavior of a filesystem that helps protect data loss. If planning to write to an HFS+ parition or drive journaling must be turned off in OSX.[12]

---

### Post by falsepod on 2011-01-20
> **mikewhatever said:**
> Be aware:

[http://en.wikipedia.org/wiki/HFS_Plus](http://en.wikipedia.org/wiki/HFS_Plus)

Thanks man :D 

Ehhhh, gonna have to reformat the drive and restore all 250+GB's of data to it D:

---

