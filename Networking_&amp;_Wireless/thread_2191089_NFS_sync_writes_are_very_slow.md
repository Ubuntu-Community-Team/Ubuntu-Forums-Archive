---
title: "NFS sync writes are very slow"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by junk.here on 2013-11-30
I moved my VMs over to an NFS v4 share the other day and discovered to my horror that VM disk IO was now less than 1 MB per second. Since transferring files to the same directories over Samba remained a zippy 100-120 MB/s, I figured the issue lay with NFS, so I did some investigating and discovered that switching NFS to async restored performance to somewhat normal levels.

That said, is there anything I can do to improve the performance of sync writes?

---

