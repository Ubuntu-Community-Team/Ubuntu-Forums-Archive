---
title: "Not authorized to mount filesystem?"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by servicetech on 2010-07-17
Just formatted and external drive partition to NTFS and am getting this message when I try to open it: Unable to mount 452 GB Filesystem, unauthorized.

Windows machines see it fine, any ideas?

---

### Post by jrothwell97 on 2010-07-17
Hazarding a guess: try rebooting and logging in as normal. It may just be temporary.

If that doesn't help, tell us a little more about your setup (connection method, Ubuntu version, etc.) and post a screenshot of the disk's partitioning scheme.

---

### Post by willjammn on 2010-07-18
I had that problem one time, and it turned out I didn't have ownership of that partition.
So I used the chown command so I was the owner.  Then was able to write to that partition.

---

