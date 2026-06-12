---
title: "ubuntu questions (round 3)"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by 29732 on 2010-08-19
hi everyone!
i have made another list of questions for everyone to answer! 


1. How can i move some space from a partition to put it as space for another partition? (basically just make a partition i want bigger)
2. What is the difference between ubuntu ultimate edition and normal ubuntu?

more questions coming soon!

---

### Post by candtalan on 2010-08-19
> **29732 said:**
> hi everyone!
1. How can i move some space from a partition to put it as space for another partition? (basically just make a partition i want bigger)


This is about making partitions to be different sizes. It can sometimes work ok, and sometimes not. It may depend on exact types of partitions and other things.

First make a backup of your data. If partition editing goes wrong you can just loose everything!

Then use a recent Ubuntu Live CD (10.04.1 is the latest) and run it live, and use the partitioner
System>Administration>Gparted partition editor

Proceed with care.

Select the partition you want to make smaller, and resize it to make space for the expanding partition.

I would then apply this to actually do it. If ok, then later I would do similar again and enlarge the second partition.

> 
2. What is the difference between ubuntu ultimate edition and normal ubuntu?


Ultimate is not Ubuntu as offered here. It is based on Ubuntu ok, no problem (good!) however it is Ubuntu with lots more bells and whistles. 

[/QUOTE] more questions coming soon![/QUOTE]

Ok!

---

### Post by 29732 on 2010-08-19
lol
thanks

---

### Post by 29732 on 2010-08-19
> **candtalan said:**
> This is about making partitions to be different sizes. It can sometimes work ok, and sometimes not. It may depend on exact types of partitions and other things.

First make a backup of your data. If partition editing goes wrong you can just loose everything!

Then use a recent Ubuntu Live CD (10.04.1 is the latest) and run it live, and use the partitioner
System>Administration>Gparted partition editor

Proceed with care.

Select the partition you want to make smaller, and resize it to make space for the expanding partition.

I would then apply this to actually do it. If ok, then later I would do similar again and enlarge the second partition.





Can you tell me it step by step?? I am a little bit of a n00b >.<
umm i have 3 partitions (1 for vista, 1 for ubuntu and 1 for vista recovery)
and vista is the partition i want to make smaller

---

### Post by linux18 on 2010-08-19
boot into a live cd, start gparted shrink the ntfs vista partition as much as you need, then expand the ubuntu partition to fill the space. however,  it is highly recommended to use vista's partitiong tool to shrink its own partition before then use the live cd to expand the ubuntu partition. Also the partitions need to be 'touching' like this:

|+++RECOVERY+++||========VISTA========||-----UBUNTU-----|  

after shrinking:

|+++RECOVERY+++||=====VISTA=====||_FREE_||-----UBUNTU------|

grow ubuntu:

|+++RECOVERY+++||======VISTA====||-----------UBUNTU-----------|

your done!



I'm ready for round 4, I haven't missed a round yet :)

---

### Post by -kg- on 2010-08-19
You might want to do some reading at the pages linked to in my signature block.

There are a number of considerations in performing partitioning operations, such as are all your partitions Primary partitions, or do you have an Extended partition?  If you have an Extended partition, is one of the partitions a Primary partition and the other a Logical partition (one which is contained within an Extended partition)?

If one is Primary and one is a Logical partition contained within an Extended partition, then it depends on which one you want to shrink and which one you want to expand.  If you're shrinking a Primary partition in order to expand a Logical, then you will have to shrink the Primary partition first, then expand the Extended partition, then finally expand the Logical partition.

If it is the reverse, then you will have to shrink the Logical partition, shrink the Extended partition, then expand the Primary.  Of course, if the 2 partitions you want to shrink/expand are not immediately next to each other, it gets more complicated yet.  You will have to shrink the one partition, expand/shrink the Extended partition, then move whatever partitions are between the two target partitions over before you can expand the other target partition into the free space.

It all depends on what you need to do.  Provide us either with the output of the command:

```
sudo fdisk -l
```
(That's a lower case "L")

...or (preferably to me) a screen shot from GParted of the target disk.  Also include which partitions you want to perform the operations on.  From that point, we can give you more of a step by step procedure.  BTW, you have four partitions...you will have a swap partition, also.  You probably don't know about it because you never see it in any listings, unless you've run fdisk -l in the past, or looked at the partitions using GParted.

Do read at the link in my signature block, though.  You might find that you'll be able to perform it yourself with a little knowledge.

One thing I will say, though...always perform the operations step by step, clicking "Apply" after each step.  Saves a lot of problems.

---

### Post by 29732 on 2010-08-19
ok but where is the partitioning tool for vista???

---

### Post by sandyd on 2010-08-19
> **29732 said:**
> ok but where is the partitioning tool for vista???

control panel -> administrative tools -> disk management. you might have to change it to icon view before you can see it.

---

### Post by 29732 on 2010-08-19
ok thanks, thanks, ill try to do the partitioning when i can

---

