---
title: "Samba transfer speed. Fast upload, slow download."
date: 2014-02-22
forum: Networking &amp; Wireless
---

### Post by cowboys4life2 on 2014-02-22
Hey everyone, got a little problem with my transfer speeds. Network is gigabit ethernet. When I'm uploading files from my Windows 7 PC to my Ubuntu server (running Ubuntu desktop), my speeds are about 90-110 MB/s. But when I try to download the same files back to my Windows 7 PC, I'm only getting 8-14 MB/s. What gives?

---

### Post by TheFu on 2014-02-23
Usually it is the side receiving the files that is the bottleneck. Either the RAM isn't being used as a disk buffer area or the HDD subsystem isn't able to write the data as quickly.
For example, my Linux CIFS server has relatively fast WD Black HDDs, so writing is at 70+MB/s, but when pulling the files back to my Windows laptop, with a WD Blue drive (and low power SATA controller), the speeds are half that.

This isn't to say that there isn't an issue, but just something to consider. To rule out the HDDs, a pure-network speed test, iperf, in both directions between the systems would be something to try.  Similarly doing local-only tests for the HDDs would be good too - bonnie++ does that.

---

