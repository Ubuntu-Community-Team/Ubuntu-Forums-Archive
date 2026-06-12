---
title: "unable to use unallocated space to increase size of /dev/sda1 with gparted"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by LTFC2020 on 2009-04-28
hi
I want to increase the size of my ubuntu partition into unallocated space but the resize/ move option is greyed out
?

---

### Post by drs305 on 2009-04-28
There is one definite and one probable cause. First, your ubuntu partition is a primary partition and the space you want is in an extended partition. You will first have to shrink sda2 (from the left) and *then *you can expand sda1.

Secondly, you can't work on your system partition unless it is unmounted. You will have to perform this operation from the LiveCD, GParted CD, SystemRescueCD, etc.

Here is an excellent guide to partitioning:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by LTFC2020 on 2009-04-28
I have been trying to do it from the live cd
the unallocated partition is greyed out in the drop down menu and the resize option is not accessible

---

### Post by plucky on 2009-04-28
**Turn off swap** even if you are using the Live CD and that should allow you to resize the extended partition.(/dev/sda2)

Then once that is done you should be able to resize /dev/sda1

Good Luck

---

### Post by scheuri on 2009-04-28
I cant see on the pic...but, do you have a separate partition for your /home? No? 
Then I suggest you do that instead of growing that partition. Upgrades and software failures can be handled easier with a separate partition for /home.

But as I said...it is not clear from the pic if you already have one or not.

cheers
scheuri

---

### Post by LTFC2020 on 2009-04-28
hi again
two questions
1, how do I turn off swap?
2, how do I create a home partition? (this sounds like a very good idea)
thanks

---

### Post by drs305 on 2009-04-28
To turn off swap, highlight it in the top graphic, right click and select "swapoff".

For moving /home to a separate partition, here is a good link:
[_http://www.psychocats.net/ubuntu/separatehome_]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by LTFC2020 on 2009-04-28
erm?!
swap off worked a treat for moving the partition
however on reboot grub error 22 and no ubuntu

---

### Post by LTFC2020 on 2009-04-28
I sorted the grub error form a quick google and everything good
thanks for the help

---

### Post by hatalar205 on 2009-04-29
> **LTFC2020 said:**
> hi
I want to increase the size of my ubuntu partition into unallocated space but the resize/ move option is greyed out
?

Your problem is **"the unallocated part must always be on the right of the part which you want to extend. Yours is on the left. So you can't."**. Unfortunately this is impossible for you. So you have to delete sda 5 and 6 and you must reparted again. Sorry.

---

