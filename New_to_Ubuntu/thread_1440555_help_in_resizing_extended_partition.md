---
title: "help in resizing extended partition"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by en_mohamed on 2010-03-27
hello dears
[SIZE=4]i have two parts of partittions
one has alinux ,and other is extended and have(three parts and unallocated area)i want to make these unallocated area to be out of extended to make it as primary partittion.

does any one can help me in this?

and other question ,i want yo resize the linux partition ,does it need to an area with ext to be merged with it or any area.
thanks advance
 
[/SIZE]

---

### Post by s_ø on 2010-03-27
yes you can resize the extended partition so the unallocated space is outside the extended.
MAKE BACKUPS.
Use GParted, select the extended partition and use move/resize. Then format the unallocated space as primary partition.

To resize the partition you need unallocated space next to it.

---

### Post by en_mohamed on 2010-03-27
> **s_ø said:**
> yes you can resize the extended partition so the unallocated space is outside the extended.
MAKE BACKUPS.
Use GParted, select the extended partition and use move/resize. Then format the unallocated space as primary partition.

To resize the partition you need unallocated space next to it.

[SIZE=4]mr s_Q thanks about your help,i did not understand what you said about  [/SIZE](resize the extended partition)[SIZE=4] when i point to unallocated area in extended the (resize/move) is not activated ,how can i moved it out the extended
would you mind to take alook on my attatchment .
thanks again
[/SIZE]

---

### Post by s_ø on 2010-03-27
You have booted the live-cd - right?
Otherwise - do it.
Do you notice the small key symbol next to extended and linux-swap? It means the partition is locked.
Right click the swap partion and select "swap off". That should remove the key symbol.
Next right click the extended partition (not the unallocated space, but where it says "/dev/sda2")  and select move/resize.

If you want the unallocated space to be merged with your sda1 partition, you need to make sure that the space is preceding not following the extended partition.


Not that it is any of my business. But why do you have two NTFS partitions inside an extended partition?
If you dont have windows installed, why even use NTFS?

---

### Post by en_mohamed on 2010-03-27
> **s_ø said:**
> You have booted the live-cd - right?
Otherwise - do it.
Do you notice the small key symbol next to extended and linux-swap? It means the partition is locked.
Right click the swap partion and select "swap off". That should remove the key symbol.
Next right click the extended partition (not the unallocated space, but where it says "/dev/sda2")  and select move/resize.

If you want the unallocated space to be merged with your sda1 partition, you need to make sure that the space is preceding not following the extended partition.


Not that it is any of my business. But why do you have two NTFS partitions inside an extended partition?
If you dont have windows installed, why even use NTFS?
i can not thank you what must to be.thanks verrrrrrrrrry much

---

### Post by s_ø on 2010-03-27
Your are welcome. If it solved your problem, please mark the thread as solved.
Select "Mark this thread as solved" from the "Thread tools" menu.

---

### Post by en_mohamed on 2010-03-27
sorry ,but last question i promise 

[SIZE=4]if i have unallocated area and i want to merge it to linux partition(ext)does it need to format unallocated first with(ext)then merge it to os,or merge unallocated first time to os.
again i promise you that is last question if my god  wanted that
[/SIZE]

---

### Post by s_ø on 2010-03-27
You can ask all you want.

First you need to have the unallocated space next to the ext partition you wish to enlarge.

Then you right-click the ext partition and select move/resize.

---

### Post by en_mohamed on 2010-03-27
> **s_ø said:**
> You can ask all you want.

First you need to have the unallocated space next to the ext partition you wish to enlarge.

Then you right-click the ext partition and select move/resize.

[SIZE=5]thanks alot again,i hope that you mean i will not format unallocated with ext and merge it without format with linux partition(that which i understand)
mr s_Q(thanks for my god first then for you about the efficient and quickly support) best wishes 
[/SIZE]

---

