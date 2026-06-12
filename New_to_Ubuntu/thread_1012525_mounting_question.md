---
title: "mounting question"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-15
This may seem like a dumb question, but is it possible to mount two drives to one mount location? To increase the storage space on a single mount.

---

### Post by Shhnap on 2008-12-15
I don't think so, though i have been wrong before. I think you could get around that by doing this:

/home/username -> mnt point 1
/home/username/exfraspacefolder -> mnt point 2

But otherwise no, i have never heard of doing that before.

---

### Post by iponeverything on 2008-12-15
LVM will allow you to add drives to an existing storage group to increase space. 

You can't just mount another drive in the same location and have its space added. Though it would be sorta cool.

---

### Post by pshootr on 2008-12-15
> **iponeverything said:**
> LVM will allow you to add drives to an existing storage group to increase space. 

You can't just mount another drive in the same location and have its space added. Though it would be sorta cool.

Yeah I thought that would be cool too. Well thanks for the info guys. Guess I will read a little about LVM

---

