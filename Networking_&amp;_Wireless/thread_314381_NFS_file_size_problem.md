---
title: "NFS file size problem"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by bobo1on1 on 2006-12-07
I have a directory on my server that is shared through nfs and mounted on my workstation.

However there is a strange problem, files bigger than 4294967296 or 2^32 bytes have the wrong file size when accessed through nfs.

Here's an example:

-rw-rw-rw- 1 1001 1001 399978496 2006-12-02 19:14 test.file

And this is what it should be:

-rw-rw-rw- 1 server server 4694945792 2006-12-02 19:14 test.file

Notice that 4694945792 - 399978496 is exactly 2^32 or 4294967296.

When I copy the files the size is still wrong, I think only the first part of the file is copied.

It looks like a bit is missing.
In the past I did not have this problem, I think it occurred after an apt-get upgrade.

---

