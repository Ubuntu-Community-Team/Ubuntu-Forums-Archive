---
title: "Creating a symlink between two partitions"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-19
So I just recently installed VirtualBox but I want to move it and all its file to my second partition on my HDD (instead of the main one they are currently on) someone on the VB forums suggested I mv all the files to the other partition and then create a symlink between the two locations. How would I go about doing this?

~Jeff

---

### Post by emarkd on 2009-01-19
I know nothing of virtualbox but if all you need is a link, you do:

```
ln -s /path/to/original /path/to/link
```

---

### Post by mjheagle8 on 2009-01-19
find it in nautilus, then right click and select create link.  rename and place the link as you would like.

---

