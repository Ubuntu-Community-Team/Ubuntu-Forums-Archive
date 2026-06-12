---
title: "Give myself writes to a whole partition"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by teranex on 2008-12-04
Hi,

During the install of Ubuntu i partitioned my hard disk in a few partitions (/, /home, swap and /media/data, all in ext3).
I'm going to use /media/data to store all my documents because i prefer to have it outside of my home folder. However i did not have write rights to the drive because it was owned by root/root. I fixed this by running `gksudo nautilus', right clicking /media/data, choosing properties, going to Permissions and setting the owner and group to my own user and group. Now i have full access to that partition, but i'm not entirely sure if this is the way to do it?

thx!

---

### Post by handydan918 on 2008-12-04
I think that should be fine, unless you need to share that partition with other users on the system or something.

---

### Post by teranex on 2008-12-04
> **handydan918 said:**
> I think that should be fine, unless you need to share that partition with other users on the system or something.
Nope, i'm the only user of the computer. Thx!

---

