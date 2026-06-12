---
title: "&quot;No root file system is defined.&quot; Error while trying to install"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Coh3n on 2010-03-05
Hello,

When I go to pick the partition to install Ubuntu to, I get this message:

"No root file system is defined.

Please correct this from the partitioning menu."

The partition I'm trying to install it to is an ext4, if that helps.

I have no clue what to do, if anyone knows please let me know. :)

---

### Post by swoll1980 on 2010-03-05
You have to pick a partition and assign it to / that will become the root partition.

---

### Post by swoll1980 on 2010-03-05
Ubuntu will do the rest for you.

---

### Post by japhyr on 2010-03-05
I am having the same trouble.  On the "Prepare partitions" screen, there is nothing to select.  Does this indicate a problem with the hard drive?

---

### Post by Coh3n on 2010-03-05
> **swoll1980 said:**
> You have to pick a partition and assign it to / that will become the root partition.
I don't know what that means.  Sorry, I don't know a whole lot about partitioning, you'll have to be patient with me.

---

### Post by PRC09 on 2010-03-05
Without seeing your exact set-up I think the problem is that the partition that you are trying to install to is already formatted ext4 as you indicated above.You should leave the partition for Ubuntu install as un-formatted and use the manual install and then partition the free space as needed,Swap,Home and /  ......

---

### Post by spiky001 on 2010-03-06
I think the op is looking for guidence on what to mark as root

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html)

and how to mark it /  I have looked for a graphical site has which actually shows it will look some more maybe some1 in forum has apic showing it

---

### Post by spiky001 on 2010-03-06
I hope this is what you want
 the / in the 2nd box indicates root making that partion root

---

### Post by Coh3n on 2010-03-06
> **spiky001 said:**
> I hope this is what you want
 the / in the 2nd box indicates root making that partion root
I know what you mean, but I didn't even have to do that.  I just deleted the partition so I had 150GB of unallocated space.  Once I ran the installer, I had the option to install the the largest continuous space (or something along those lines).  So everything good, I got it figured out.

Thanks everyone,
Coh3n

---

