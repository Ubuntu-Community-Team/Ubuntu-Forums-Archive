---
title: "Ubuntu nfs server and statfs from vxWorks"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by dhuynh on 2008-08-13
Hi all,
I have an nfs client runs on vxWorks 6.2 and nfs server on Ubuntu.  I don't know what version of nfs runs on Ubuntu, but on vxWorks 6.2, it runs nfs3.  I can mount (from vxWorks to Ubuntu) and access the mounted folders just fine, the problem is that when I issue the statfs command on the mounted directory, the returned [statfs structure]("http://linux.die.net/man/2/statfs")'s f_blocks, f_bfree, and f_bavail are negative.

Ubuntu's export file:
/home *(rw,async,no_root_squash,no_subtree_check)

Please lemme know if any of you run into the similar.

Thanks

---

