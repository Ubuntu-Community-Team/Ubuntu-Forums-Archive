---
title: "torrents make internet slow"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by zenkaon on 2008-02-04
Hello,

Does anybody know why the rest of the internet slows down so much when I'm downloading torrents?

If I am downloading torrents at say, 20 KB/s, then webpages take ages and ages to load and remote ssh connections have a real latency. I'm on 2 MB virgin media internet,  I usually get 260 KB/s downloads - so I do have the bandwidth.

Same slowness using azures or ktorrent. Noticed this using ubuntu 7.04, 7.10 and before that using RHEL4 and RHEL5 (in the bad old days of RPMs). So this doesn't seem to be an ubuntu specific problem, something with Linux in general.

My dad uses XP and doesn't see his internet slow down too much when downloading torrents with azures.

---

### Post by tbfr on 2008-02-04
1. Did you try to limit the upload speed? The upload bandwidth is usually smaller than the download bandwidth and may be a limiting factor.

2. If 1 didn't work, try lowering the number of max connections. Maybe your router can't handle that many connections.

---

