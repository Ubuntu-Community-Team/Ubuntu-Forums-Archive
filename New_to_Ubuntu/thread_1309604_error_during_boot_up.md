---
title: "error during boot up"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by libihero on 2009-11-01
this error comes up when i try start the computer

---

### Post by libihero on 2009-11-01
im attaching again

(edit) sorry for that, it gave me an error for my first attachment but it looks like it worked

---

### Post by libihero on 2009-11-25
bump.....

---

### Post by pi.boy.travis on 2009-11-25
Try holding down SHIFT at startup, and selecting the (Recovery Mode) option.

---

### Post by libihero on 2009-11-27
didnt work :(

---

### Post by sandyd on 2009-11-27
> **libihero said:**
> bump.....
its a bug thats been running around for some time now.
drop to a recovery shell.
and run this
```

sudo fdisk -l
//write down your linux partition /dev/sdaxx
sudo fsck -y /dev/sdaxx\
```

oh, and if your curious about the bug....
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/58430](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/58430)

---

