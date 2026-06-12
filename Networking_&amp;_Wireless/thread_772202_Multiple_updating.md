---
title: "Multiple updating?"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by almkglor on 2008-04-28
A small local company's CTO has finally decided to install Ubuntu 8.04 as a dualboot on all their current Windows systems (ha, ha, I'm the CTO/CEO's and the CFO's son, and the company has about a dozen employees...).  However, his concern is largely with the updating of the various parts in the system - there are about 4-5 computers to be installed with various versions of Ubuntu (servers and desktops, with a mix of 32-bit and 64-bit).

Since my own personal computer has been updating for two days straight (obviously our internet connection isn't the fastest, just the fastest they can afford), his concerns are quite valid.  If we could download the update packages on one computer, and then have the updating from the packages, it would be better, but how feasible is this?

---

### Post by ryanhaigh on 2008-04-28
You may want to look at aptoncd, apt-mirror, apt-cacher and apt-proxy. These are all good ways to setup this kind of thing. The less well managed way is to copy the packages is /var/cache/apt/archives.

---

