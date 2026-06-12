---
title: "k9copy temp file too small"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by trugreg on 2009-04-17
I get error - Insufficient disk space on /tmp/kde-greg/k9copy/
4,400 mb expected.  How do I increase the disk space for this?

---

### Post by ashmew2 on 2009-04-19
I'm guessing that you've run out of space on your root directory. ( the / partition). It has less than 4400 MB and k9copy requires at least that much amount for the requested operation.
I think you could try changing k9copy's default directory to something like /home where you have enough disc space.

Also , you could consider resizing your / partition although i would strongly recommend NOT DOING IT because you could seriously lose data.

---

