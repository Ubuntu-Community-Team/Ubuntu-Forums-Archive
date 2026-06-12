---
title: "Change allocated disk space"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by samoht83 on 2011-08-24
When doing a dual boot Ubuntu install it lets you choose how much of your C drive you want to be allocated to Ubuntu. Is there a way to change this without reinstalling? I need to allocated more of my C drive to Ubuntu.

---

### Post by Basher101 on 2011-08-24
What windows do you use?

---

### Post by samoht83 on 2011-08-24
Using windows vista.

---

### Post by bhaverkamp on 2011-08-24
gparted -- a backup is always wise. Make sure last windows shutdown was clean. Shrink windows partition by moving end of partition. Then resize Ubuntu partition by moving leading edge of partition.

---

### Post by Mark Phelps on 2011-08-24
> **samoht83 said:**
> Using windows vista.

Then, it would be best NOT to use GParted or the Ubuntu installer to shrink your Vista partition.  Doing so risks corrupting the Vista OS partition and rendering it unbootable.

Instead, use the Vista Disk Management utility.  That will give you less flexibility, but it won't risk damaging the partition.

---

### Post by Basher101 on 2011-08-24
Before you do any partitioning, make sure you ***_[SIZE="4"]defrag[/SIZE]_*** before that

---

### Post by samoht83 on 2011-08-24
Thanks guys Ill give that a try.  I haven't installed many items on ubuntu yet would it be easier and less damaging just to use the control panel on vista and uninstall ubuntu and reinstall it and choose more disk space to use?

---

