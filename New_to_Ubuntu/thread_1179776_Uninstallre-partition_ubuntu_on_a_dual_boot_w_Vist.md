---
title: "Uninstall/re-partition ubuntu on a dual boot /w Vista"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by jjunos on 2009-06-06
So after a week of struggle with Ubuntu, I'm looking for some suggestions/answers/anything!

Trying to get advice on re-partitioning my ubuntu install.

Newest build of ubuntu, i have it dual booting. But i choose the "default" install of having it next to vista. I wasn't aware that you needed to give it more space than what it was originally set o.

To say the least, the first day I put all my programs, and try to update, ubuntu tells me I am out of space. Looking at it, it says I gave the vista loader 1.5 gigs (which seems small), and Ubuntu 2.5 gigs (with 170+ gigs just sitting there).

Is there any way to increase the size of the partition of Ubuntu (and probably vista too...)?

---

### Post by k_squired on 2009-06-06
I would suggest looking for an external partitioner tool.  I've heard of parted magic, which is a RAM-resident linux distribution just for partitioning things, but be careful, as there are some known bugs in the system itself, at least (I suppose the partitioner itself is supposed to work - read up on that) which I never used actually to partition anything.

Oh, and word has it that it can really slow down your other installation, at least if you don't give it enough room.  Look into that a little as well.

And as I'm sure you already know: be EXTREMELY careful when working with drive partitions unless you don't mind loosing/damaging all the data on that disk!

If you did not invest anything in it, perhaps you could reinstall Ubuntu in a larger partition over the old installation, directly from the installer.

Good luck.

---

### Post by QIII on 2009-06-06
Before you do anything at all:

Get every tiny little thing you may want from Windows and back it up to removable media.  

While there are tools to recover files when you delete or overwrite partitions, it's best to just save yourself the heartache.

---

### Post by jjunos on 2009-06-06
> **k_squired said:**
> I would suggest looking for an external partitioner tool.  I've heard of parted magic, which is a RAM-resident linux distribution just for partitioning things, but be careful, as there are some known bugs in the system itself, at least (I suppose the partitioner itself is supposed to work - read up on that) which I never used actually to partition anything.

Oh, and word has it that it can really slow down your other installation, at least if you don't give it enough room.  Look into that a little as well.

And as I'm sure you already know: be EXTREMELY careful when working with drive partitions unless you don't mind loosing/damaging all the data on that disk!

If you did not invest anything in it, perhaps you could reinstall Ubuntu in a larger partition over the old installation, directly from the installer.

Good luck.

Yeah, luckily it's a new dev box for me, so it's more or less trying to save the time I've invested so far. 

Is it possible to uninstall Ubuntu and return it to a state before I did the dual boot, and then reinstall Ubuntu? Or is there an option to install over the old Ubuntu install when I try to install Ubuntu? I tried re-installing, and I simply got to the screen for partioning again, and it mentioned that I had multiple OS's installed already....

---

### Post by theozzlives on 2009-06-06
Vista comes with it's own partition resizing tool. Use Partition Editor off the live CD to resize Ubuntu. If you do re-install, make yourself a separate /home partition.

---

### Post by jjunos on 2009-06-08
> **theozzlives said:**
> Vista comes with it's own partition resizing tool. Use Partition Editor off the live CD to resize Ubuntu. If you do re-install, make yourself a separate /home partition.

What is the partition for Ubuntu called?

I checked my partitions, and I have a 2.32 gig unnamed partition (which I assume is Ubuntu). But vista won't give me any options other than to delete the partition. And yes, I shrunk another partition to give me 20 gigs of unallocated space.

If I just delete the Ubuntu partition, what happens when I try to boot? Will that kill my box?

---

### Post by LewRockwell on 2009-06-08
we could always use information like the output of:
```
sudo fdisk -l
```
(that's a little "L" and NOT a one or an eye)

and/or a screen-shot of gparted...

---

### Post by jjunos on 2009-06-08
> **LewRockwell said:**
> we could always use information like the output of:
```
sudo fdisk -l
```(that's a little "L" and NOT a one or an eye)

and/or a screen-shot of gparted...

Up and running.


Ended up going:

1. Deleting the partition in Vista that I believe was the Ubuntu install (a 2.5 gig partition that was not assigned a drive and not named).

2. Which left grub (which I believe is the loader?) on the box. 

3. put the Ubuntu install in, and simply reinstalled everything, but this time ensuring I gave Ubuntu space to stretch it's legs (70gigs).

End result:

I lost all my work on the Ubuntu install (which was fine since there wasn't much on it), and the reinstaller properly (at least I think it did) re-partitioned my hd to give ubuntu more space.


Thanks for everyones suggestions!

---

