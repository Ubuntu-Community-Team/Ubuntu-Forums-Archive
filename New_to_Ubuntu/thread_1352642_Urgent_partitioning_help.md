---
title: "Urgent partitioning help"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-11
How do I merge the unallocated partition into my primary partition? Its not allowing me to reduce the size of the extended partition. See attached screenshot.

---

### Post by audiomick on 2009-12-11
You want the unallocated space in sda1?
try this:
move the right side of sda6 to the right to take over the unallocated space.
move the left side of sda6 to the right.
move the right side of sda 1 to the right.

I believe it is something like that.

---

### Post by bumanie on 2009-12-11
Not sure it is worth the effort seeing it is only 1GB in size. However the difficulty you are having in changing partitions is due to the fact that you have installed ubuntu within a logical partition - I don't think you can change the size of a logical partition. The other thing, it is not possible to alter a filesystem that is active, therefore you need to do the partitioning off a live cd, either the ubuntu live cd or the dedicated gparted live cd. Here you'll find the [gparted manual]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html") - give it a read.

---

### Post by audiomick on 2009-12-11
@ bumanie
i'm guessing that the problem is the the / on sda1 is full, and he needs the space for that.

He is running from the live cd, from the look of the screenshot, and none of the partitions are mounted. If they are, there is a picture of two keys next to them.

@ rkakkar
the suggestion to read the gparted manual is a good one...;)

---

### Post by rkakkar on 2009-12-11
> **audiomick said:**
> You want the unallocated space in sda1?
try this:
move the right side of sda6 to the right to take over the unallocated space.
move the left side of sda6 to the right.
move the right side of sda 1 to the right.

I believe it is something like that.


this worked! thanks :)

---

