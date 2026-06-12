---
title: "Can't access hard drive when using linux from a flash drive."
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Zephyr618 on 2009-05-08
I put ubuntu on a flash drive. It works fine except that when I try to access the hard drive that is on my computer it says that it cannot mount the hard drive because it is already mounted on /media/disk/, this is impossible because there is no such folder. What is wrong and how can I fix it.

---

### Post by taurus on 2009-05-08
What are the outputs of these commands from a terminal, running one at a time?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

