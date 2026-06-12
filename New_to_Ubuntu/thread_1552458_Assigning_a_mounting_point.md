---
title: "Assigning a mounting point"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by kalebka55 on 2010-08-13
Hiya,  I have just recently resized (freed up some unallocated space) a partition using gParted.  I successfully allocated the space I require.  Now,  I tried to mount the original partition back but the mounting point details were removed.  how do i assign a mounting point? do i need to?

Help appreciated!

---

### Post by cj13579 on 2010-08-13
If your new partition is called, for instance, sdb1. you can mount it at location "newpartition" with

```
sudo mount /dev/sdb1 /media/newpartition
```

You will need to create the directory /media/newpartition with

```
sudo mkdir /media/newpartition
```

you can give it universal read/write access with

```
sudo chmod -R 777 /media/newpartition
```

You will need to modify your fstab to automount this partiton on bootup.

---

