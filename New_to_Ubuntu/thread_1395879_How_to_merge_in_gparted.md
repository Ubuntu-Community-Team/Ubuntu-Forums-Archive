---
title: "How to merge in gparted"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by jbalazs on 2010-02-01
I just deleted Windows partition and reformatted it to ext4 now how can I merge

it with the partition that Ubuntu 9.10 is ??  

Thanks

---

### Post by audiomick on 2010-02-01
Hi.
If you want to "merge", you have to delete the partition completely and grow the Ubuntu partition into the empty space.

---

### Post by drs305 on 2010-02-01
I wrote a guide for expanding the / (system) partition a while back in response to a bug in the Jaunty installation process.

It covers how to expand the system partition, taking space from Windows. The procedures and techniques would apply equally to your situation. The actual steps begin about half way through the post.

Here is the link:  [http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

If you need more responses in this thread, it would be helpful to provide a screenshot of Gparted or as a minimum the results of:
```
sudo fdisk -l
```
# Lowercase L

---

### Post by jbalazs on 2010-02-01
Thanks it's solved

---

