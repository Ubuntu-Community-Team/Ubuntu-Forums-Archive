---
title: "ext3 freespace to fat32"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by ashwat on 2009-03-15
My entire HDD is of a single ext3 partition. There are certain things that I cannot get to work using VirtualBox and I need to install Windows and seems like the install disk fails to recognize the presence of a HDD. So I would like to create a FAT32 partition from the freespace on the ext3 and set up a dual boot. How should I go about doing this?

---

### Post by SuperSonic4 on 2009-03-15
I'd get the live cd or the gparted live cd and shrink the ext3 partition but however much you want. You can then format the free space using fat32 and then get the xp cd and install.

---

### Post by jelle_ on 2009-03-15
boot from ubuntu live-cd. 
open gparted to shrink ubuntu and create a fat32-partition

---

### Post by ashwat on 2009-03-15
thanks guys. will get working on that immediately.

---

### Post by SuperSonic4 on 2009-03-15
As with any partitioning backup important data first. You *shouldn't* lose any data but there is always a risk

---

### Post by egalvan on 2009-03-15
[QUOTE=ashwat;6900361 So I would like to create a **FAT32** partition from the freespace on the ext3 and set up a dual boot. How should I go about doing this?[/QUOTE]


Unless you have a particular NEED for FAT32,
I would suggest NTFS instead.

---

