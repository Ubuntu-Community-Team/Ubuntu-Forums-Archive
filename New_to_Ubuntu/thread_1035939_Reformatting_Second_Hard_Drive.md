---
title: "Reformatting Second Hard Drive"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by mojo_man on 2009-01-10
Hi,

I put in a second hard drive in my system and I want to use it to house a virtual machine. I would like to reformat it with ext3. How do I go about it doing it?

I am running Ubuntu 8.10

---

### Post by wolfen69 on 2009-01-10
```
sudo apt-get install gparted
```then
```
gksudo gparted
``` pick the drive you want, right click it, choose unmount, then right click again for all the options you will need.

---

### Post by snova on 2009-01-10
> **mojo_man said:**
> Hi,

I put in a second hard drive in my system and I want to use it to house a virtual machine. I would like to reformat it with ext3. How do I go about it doing it?

I am running Ubuntu 8.10

Depending on the VM software you use, this might not even be the right thing to do. All software I know of uses a big file on your HD to represent the guest OS's hard disk. They don't use actual partitions.

Unless, of course, you wanted to store the file itself on the external- in which case, never mind. :)

---

