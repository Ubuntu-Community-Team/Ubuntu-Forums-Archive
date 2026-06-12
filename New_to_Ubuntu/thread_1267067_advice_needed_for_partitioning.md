---
title: "advice needed for partitioning"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by zack_kv on 2009-09-15
I have a ubuntu 9.04 installed on the server which has hardware raid 10 installed on it. This is going to be a Lamp server. I wanted to separate the operating system from the data. 
Would it be a good idea to have one physical partition and have lvm on it? Make logical partitions using lvcreate as follows--
root
swap
db1
db2
backup

There is only one physical partition /dev/sda.
Would it be better to have physical partitions rather than the logical partitions like it is presently configured?

---

### Post by Boondoklife on 2009-09-15
Well I personally love LVM but that is really only because we do alot of drive changing etc here, If you do not plan on doing this then just do it with normal partitions. Your HWRAID10 will take care of rebuilding the raids and what not so i dont see a need.

---

### Post by zack_kv on 2009-09-16
I am planning on sticking to lvm. I want some sort of flexibility. I guess even if the os gets corrupted ubuntu is smart enough to recover data from other partitions on lvm.

---

