---
title: "GParted help"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by tega2919 on 2010-05-13
I have a computer running windows 7 and Ubuntu. with about 130 GB on windows and 100 GB on ubuntu. Why does Gparted show my hard drive as 230 gigs of unpartitioned space?

---

### Post by srs5694 on 2010-05-13
This is a recurrent problem. It's usually caused by a combination of a bad partition table and a bug in GParted. Try typing "sudo fdisk -lu" at a shell prompt and post the results between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string so that we can see the technical details of your partitions. Chances are somebody will be able to offer a solution.

---

