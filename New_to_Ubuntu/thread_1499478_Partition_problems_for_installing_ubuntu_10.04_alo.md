---
title: "Partition problems for installing ubuntu 10.04 alongside Windows 7"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Goldwolferadior on 2010-06-01
I have Windows 7 installed on my laptop. The trouble is that when I try to install 10.04, I can't make a partition at all. I go into Gparted, and when I try to make a new partition out of some free space I have, I get an error message saying that there four partitions on the drive and that I can't make a new one.

Is there any way to fix this problem without having to delete any partitions?

---

### Post by hortstu on 2010-06-01
I think you need to make an extended partition and move one of the existing partitions into it...  I'm a bit of a newb so I don't even know if that's possible.  Make sure you back everything up before you do this.

From what I understand you can put as many partitions as you want inside an extended partition.

I make my entire drive an extended partition and then break it up from there so I don't have any limitations on the number of partitions I can have.

Good luck and just to be on the safe side wait for another answer.

---

### Post by Mark Phelps on 2010-06-02
> **Goldwolferadior said:**
> Is there any way to fix this problem without having to delete any partitions?

Basically, no.  You would have to delete a primary partition, create an extended partition, recreate the primary as a logical inside the extended, and copy the data back to the logical from the former primary.

Also, be sure to use the Win7 Disk Management utility to do partition shrinkage and movement; do NOT use Gparted to do that.

---

### Post by srs5694 on 2010-06-02
It's sometimes possible to convert a primary partition into a logical partition, but the procedure is a bit tricky, at least with the tools I know of that can do the job. Please post the output of the "sudo fdisk -lu" command when typed at a Linux text-mode shell prompt. (That'a s lowercase "LU", and there's a space between "fdisk" and "-lu".)

Chances are you'll be able to delete at least one of those partitions, since one of them probably holds an on-disk equivalent of your Windows installation DVD. If you didn't receive such a DVD with the computer, you can locate a utility in Windows to create a set of DVDs. (I recommend creating two sets, since recordable DVDs aren't as reliable as DVDs pressed at a factory.) It should then be safe to delete the partition on which those files reside, resize and perhaps move other partition(s), create an extended partition in the free space, and create Linux and shared-data partitions in the extended partition.

---

### Post by Nidwow on 2010-06-02
> **Mark Phelps said:**
>  
Also, be sure to use the Win7 Disk Management utility to do partition shrinkage and movement; do NOT use Gparted to do that.
 
+1
 
Windows 7 disk managment shrink is the way to go and it only take a few mins to do it. :guitar:

---

### Post by Goldwolferadior on 2010-06-14
> **Mark Phelps said:**
> Basically, no.  You would have to delete a primary partition, create an extended partition, recreate the primary as a logical inside the extended, and copy the data back to the logical from the former primary.

Also, be sure to use the Win7 Disk Management utility to do partition shrinkage and movement; do NOT use Gparted to do that.

OK, will do then.

Thanks for all the responses.

---

