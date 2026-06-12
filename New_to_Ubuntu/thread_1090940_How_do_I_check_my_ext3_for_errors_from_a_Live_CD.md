---
title: "How do I check my ext3 for errors from a Live CD?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by diablo75 on 2009-03-08
I'm having some really strange problems with my computer today and want to check the hard drive for errors after booting from a Live CD.  Is this possible?

---

### Post by taurus on 2009-03-08
You mean running fsck.

```
sudo fsck /dev/sda1
```
If /dev/sda1 is the ext3 filesystem you want to check.

---

