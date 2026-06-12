---
title: "dosfsck &quot;Reclaiming Unconnected Clusters&quot;"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by brtomkin on 2010-05-03
I am performing a disk check on an external usb hard drive (fat 32) that seems to have become corrupted (data loss).  With the drive unmounted, I run the following command in a terminal:

sudo dosfsck -v -a /dev/sdb1

It starts running and gets as far as "Reclaiming Unconnected Clusters" but then seems to get stuck.  I have a couple of questions.

1.  What does "Reclaiming Unconnected Clusters" mean?

2.  It is a large drive ~500 Gb so I expect it to take a while, but how long should it take?  I have been waiting for 2 days.

Thanks for any help or info!

---

