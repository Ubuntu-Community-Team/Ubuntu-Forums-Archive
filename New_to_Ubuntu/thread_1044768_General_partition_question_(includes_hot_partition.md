---
title: "General partition question (includes hot partition pr0n)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by cyan on 2009-01-19
Below is a smokin' hot picture of my partitions on a dual boot system.

[IMG]http://copilyanez.com/images/Screenshot3.png[/IMG] 

All of my Linux install is under sda2.  If I want to add another distro, should I create a new partition (presumably labeled sda3)?  Or can I add it inside sda2?

And is it generally a good idea to have your / and swap under the same extended partition? Or should they be in separate partitions?

Thanks for helping us noobs, we are hot for Linux but aren't always experienced.

---

### Post by drs305 on 2009-01-19
If you are going to add another distro create a new partition. I would opt for another logical partition rather just for more flexibility down the road (if you decide to divide it again).

There is no need to put the swap partition elsewhere (in the primary partition area for instance) for operational purposes. You may want it there so the designation doesn't change but that is a minor consideration.

Note that if you create a new logical partition the "sda6" designation of your swap may change or you may get a "partitions are not in disk order" message when running the "fdisk" command. This isn't a problem if you are using UUIDs to identify everything.
Added: You could avoid both those issues by shrinking sda5 and then moving the swap partition up against sda5 first. If using gparted, select "swapoff" before moving the partition - otherwise run "sudo swapoff -a" first to unmount it.

Welcome to ubuntu. :-)

---

### Post by cyan on 2009-01-19
drs305,

Thank you!  If I understand you correctly, you are saying that I should add a completely new partition (instead of just making space in sda2 and formating as EXT3) correct?  Does that mean that I would also be setting up a new swap when I install the new distro?  Or can the new distro use the existing swap in sda2?

Thanks again for helping, I want to understand enough so that I don't limit myself later.

---

### Post by drs305 on 2009-01-19
I would make a separate partition for any new operating system. They can share the same swap partition. I am not sure I understand the "making space in sda2" comment - that would include making a new partition as well. The advantage of putting it in the extended partition is that you can have many logical partitions and aren't limited in number as you would be for primary partitions (even though you have 2 remaining there). Besides flexibility in numbers, you also have more capability to expand a partition in the extended partition that you will in the primary partition.

If by new operating systems you are speaking of kubuntu or xubuntu with an established ubuntu system, you can just add the appropriate desktop rather than install the entire OS. The version you wished to use would be selected when establishing the session.

---

### Post by cyan on 2009-01-19
Thanks again.  I am still having trouble understanding this conceptually, however.  Sorry to belabor the point but would my new set up look like this (ignoring the actual drive number for now)?

[I]sda1 (NTFS)

sda2 (extended)
..sda5 (ext3)
..unallocated
..sda6 (swap)

sda3 (extended)
..sda7 (ext3) - new linux distro to go here
[/I]
Or like this:

sda1 (NTFS)
[I]
sda2 (extended)
..sda5 (ext3)
..unallocated
..sda6 (swap)
..sda7 (ext3) - new linux distro to go here[/I]

And is there a preference?

---

### Post by drs305 on 2009-01-19
It's much a matter of preference. You can get different opinions.

With waht you already have, I'd probably set it up this way:

sda1
sda2 ext
sda5 linux (leaving room for expansion)
sda7 unallocated or data
sda8 new OS
sd6 swap

You would have to move as little as possible this way. By placing the unallocated or data partition as sda7 (between) you could take space from it for either 5 or 8 if your space needs change.

Once I had the partitions set up I would probably run fdisk to get the partitions in numerical order.

---

### Post by cyan on 2009-01-19
You are my new hero.

Thank you so much for the advice.  So it's not a really big deal to do it either way.  You are correct that keeping all linux stuff under sda2 would probably be the least amount of hassle.

Thank you so much!  I love Ubuntu and I love this community!

---

