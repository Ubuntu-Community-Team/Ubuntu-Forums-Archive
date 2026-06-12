---
title: "File Sharing with XP"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by ericstrom on 2010-01-23
I'm a little confused on the file system. Just set up Jaunty to dual boot with Windows XP. It seems Jaunty is sharing files with XP. That's resulting in getting a message that my disk is full. How do I stop Jaunty from sharing files with XP ?

---

### Post by cariboo on 2010-01-23
How did you install Jaunty? Inside Windows (wubi) or as a separate installation on a partition of it's own?

---

### Post by mharrison on 2010-01-23
Can you post the results of:

```
sudo fdisk -l
```

That is a lowercase L

It's possible you didn't create the / or /home partitions to be large enough.

---

