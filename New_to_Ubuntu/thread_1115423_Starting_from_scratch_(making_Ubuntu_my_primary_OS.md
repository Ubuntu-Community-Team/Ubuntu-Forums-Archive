---
title: "Starting from scratch (making Ubuntu my primary OS and ditching Windows XP)"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by the aftermath on 2009-04-03
Here's my situation. I have Windows XP on my PC and sbout a week ago I installed Ubuntu 8.10 onto a 15gb partition. I've decided I'd like to ditch Windows completely and just stick with Windows. I've already backed up all my documents from the Windows side of things, so that's not a problem. I've also burned an Ubuntu boot disk. How do I go about making Ubuntu my primary OS and deleting XP? Do I have to delete everything and start from scratch? Thanks in advance.

---

### Post by halitech on 2009-04-03
there are 2 ways you could do this. 

1. Boot from the install cd and install using the entire disk (basically starting over from scratch)

2. Boot from the Live CD, use Gparted to remove the windows partition and then format it with EXT3 and mount it in fstab as an extra data partition. You may also want to edit GRUB to get rid of the windows section.

---

### Post by the aftermath on 2009-04-04
> **halitech said:**
> there are 2 ways you could do this. 

1. Boot from the install cd and install using the entire disk (basically starting over from scratch)

I ended up going with this method. Thanks. :KS

---

### Post by billgoldberg on 2009-04-04
> **the aftermath said:**
> I ended up going with this method. Thanks. :KS

It was the easy thing to do :p

---

