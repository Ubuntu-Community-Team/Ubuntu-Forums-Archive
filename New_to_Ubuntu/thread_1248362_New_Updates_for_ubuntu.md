---
title: "New Updates for ubuntu"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by Deathtrp123 on 2009-08-24
I'm thinking the guided partition did not allow enough memory for ubuntu to work correctly on my computer.(It only did the minimum allocation)I need more space for the newest updates and I tried freeing up some space from windows vista. I shrank some of my hard disk drive partition and it worked only what format does the new partition have to be in for ubuntu to find it and use it? Was unallocated is now ext2 after using gpartion. ?Help?:confused:

---

### Post by theozzlives on 2009-08-24
All you do is use gparted, shrink your Windows and grow your Ubuntu. You already shrunk Windows. Get rid of that ext2 and grow your root (/) partition.

---

### Post by Copernicus1234 on 2009-08-24
ext2 can be used by Ubuntu, even though its better to use ext3 or ext4 since its newer and better.

Anyway, you need to mount your new partion for Ubuntu to be able to see it. You can google on how to do that, its not hard.

theozzlives advice is even better if you want extra space on the same partion you use now for the system.

---

### Post by t0p on 2009-08-24
A terminology tip for ya OP.  "Memory" refers to RAM, not disk space.  Unless you are talking about swap.  But you weren't, were you?

---

### Post by 3rdalbum on 2009-08-24
> **Deathtrp123 said:**
> I'm thinking the guided partition did not allow enough memory for ubuntu to work correctly on my computer.(It only did the minimum allocation)

The guided partitioning did exactly what you told it to do, because you didn't move the little slider to the left to allocate Ubuntu some more space.

The slider is on the bar chart at the bottom of the "Guided or Manual partitining" screen.

---

