---
title: "Had to move around some partitions, now ubuntu does not mount Swap partition :("
date: 2009-05-16
forum: New to Ubuntu
---

### Post by rob1101 on 2009-05-16
I recently had to move around some partitions and resize a few because windows 7 is ridiculous in that it takes 20+ gigs just for an install :evil:, anyway I had to temporally move the swap (delete and recreate it). Now ubuntu will not mount it when I boot and I thought I would be alright seeing as I have 4gigs of ram but it seems some apps just refuse to preform well without swap... How do I go about fixing this?

---

### Post by egalvan on 2009-05-16
> **rob1101 said:**
> move the swap (**delete and recreate** it). Now ubuntu will not mount it when I boot 

swap is handled by fstab,
and, by default, fstab uses UUID's to identify partitions...

When you delete a partition, it's UUID disapears forever.

your swap now has a new UUID.

run 

```
sudo blkid

```
and this will give you the UUID's of every partition available.

cut and paste the correct UUID into fstab, and this should take care of the problem.


note, use

```
gksudo gedit /etc/fstab
```

to edit fstab.


personally, I use LABEL instead of UUID to identify partitions.

---

### Post by Bölvaður on 2009-05-16
this is from "man swapon"

>        -a     All devices marked as ‘‘swap’’ in /etc/fstab are made available,
              except for those with the ‘‘noauto’’ option.  Devices  that  are
              already being used as swap are silently skipped.


make sure you got your swap in fstab

this command might help you

```
sudo blkid

```

---

### Post by rob1101 on 2009-05-16
Thanks guys Ubutuforums.org proves once again that its the best place one the web :)

---

### Post by Hilko on 2009-12-07
Thanks ! The forums are great indeed.
Just one question. After running 'sudo blkid' i see all my partitions and uuid's, but at the end there is this line:
 ```
/dev/ramzswap0: TYPE="swap"
```
What is this ? What does this mean ?

---

