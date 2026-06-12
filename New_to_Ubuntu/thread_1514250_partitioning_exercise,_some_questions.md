---
title: "partitioning exercise, some questions"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Ariakkas on 2010-06-20
i have an old p3 that im playing with, trying to learn how to manipulate partitions myself. this is purely for educational purposed and dont really care if i bork the whole thing

i set up a dual boot with ubuntu 9.10 and crunchbang. i created a gparted live cd, and booted to it.

the goal was to erase ubuntu, and have crunchbang take up the rest of the free space.

heres where im at.

/dev/sda1 (ext3)---had ubuntu now is empty partition
/dev/sda2 (extended)
 /dev/sda6 (ext3)---crunchbang(i think)
 /dev/sda5 (linux-swap)---swap

i have tried everything with sda1, deleting the partition and trying to grow sda6 to take up the unallocated space, tried creating sda1, shrinking sda6 and moving the shaded part to the far right, then having sda1 grow and take up the space.....
all i am able to do is grow, shrink and move within each of the 2 main partitions.

for example...sda1 is 15gb, i can do whatever i want, but i cant go over 15 gb, regardless of how much unallocated or partitioned space is available.

i feel like im missing an "aha!" moment somewhere

heres how the partition map looks

[/dev/sda1 15.26gb][/dev/sda6 22.12gb][] <---swap

any help is appreciated.

---

### Post by Bachstelze on 2010-06-20
And what is the extended partition for?

I'll tell you. ;) The extended partition acts as a container for your logical partitions (sda5 and sda6), but not for your primary partition, sda1 (i.e. sda1 is *outside* the extended partition). This means that if you delete sda1, you will have free space *outside* the extended partition. This, in turn, means that you will not be able to just "give" that space back to sda6, because being a logical partition, sda6 can only exist inside the extended partition.

From there, it should be obvious what you need to do: first, you must grow your extended partition (sda2) so it takes up the space previously taken by sda1. Then you should be able to grow sda6 to fill up that space.

---

### Post by Ariakkas on 2010-06-20
that made total sense, you rock!

i had actually attempted something similar to this, but with the partition being there, and not being unallocated space.

deleted sda1, grew sda2, then grew sda6 to match.

thanks a ton

---

