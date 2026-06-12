---
title: "Partition Editor &amp; File Manager report different HD info"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by decomp on 2009-12-02
Hi,

I have one hard drive with two partitions. My main partition, which according to GParted is 35.69 Gb, and then a swap (which according to GParted is 1.57 Gb.)

When I check the free space on my main partition by looking at GParted, it reports that my main partition is 35.69 Gb with 14.52 Gb unused. 

When I browse to my home directory, right click and select 'properties' in my file manager, it reports a 38Gb 'volume' with 12.7 Gb free space. Why the discrepancy in free/unused space?

Thanks in advance!

BTW: I'm running Ubuntu 9.04 with ext4 filesystem

---

### Post by ukripper on 2009-12-02
Go to terminal and post output of this command:
```
df -h
```

---

