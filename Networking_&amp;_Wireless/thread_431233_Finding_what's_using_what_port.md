---
title: "Finding what's using what port"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by gjtoth on 2007-05-02
I'm attempting to run an smtp proxy however, I'm getting told that port 25 is in use.  I've checked my processes and I don't THINK I'm running anything that uses that port.  Is there a console command I can use to find out what's using what on what port?

---

### Post by lloyd_b on 2007-05-03
Try "netstat -p", and look at the entries with a "proto" of "tcp".  With any luck, this will tell you exactly which program is hogging that port.

Lloyd B.

---

### Post by gjtoth on 2007-05-03
> **lloyd_b said:**
> Try "netstat -p", and look at the entries with a "proto" of "tcp".  With any luck, this will tell you exactly which program is hogging that port.

Lloyd B.


Thanks, Lloyd.  Much appreciated.

---

