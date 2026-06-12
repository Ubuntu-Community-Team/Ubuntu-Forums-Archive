---
title: "Shrinking Partition"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Nickjpost on 2010-11-29
Hello and good day!
I am planning to dual boot my Ubuntu 10.04 with Fedora 14. There is an option during install that allows for shrinking the current system...my question is though, will it do so non-destructively? 

Thank you in advance!!

---

### Post by ajgreeny on 2010-11-29
> **Nickjpost said:**
> Hello and good day!
I am planning to dual boot my Ubuntu 10.04 with Fedora 14. There is an option during install that allows for shrinking the current system...my question is though, will it do so non-destructively? 

Thank you in advance!!
It should be easy, I think, though it's a long time since I looked at the Fedora installation system.

However, I prefer using gparted from a live CD or USB to shrink and edit partitions before I install a new OS;  it gives me more confidence in what is happening, and allows me to choose specific partitions which already exist on the disk.

---

### Post by stefangr1 on 2010-11-29
> **Nickjpost said:**
> Hello and good day!
I am planning to dual boot my Ubuntu 10.04 with Fedora 14. There is an option during install that allows for shrinking the current system...my question is though, will it do so non-destructively? 

Thank you in advance!!

It will do so nondestructively, and it should have a high success probability. You should, however, keep in mind that shrinking a partition is a high risk operation that you should not try without making a backup of all important data. Also, it may take a (very) long time, as all data on the part reserved for the new partition has to be moved.

You should under no circumstances reset your computer if you get the idea that shrinking is taking too long! I remember some recent posts of people who did that. Not pretty...

---

### Post by Nickjpost on 2010-11-29
Thank you both for the suggestions!

---

### Post by matt_symes on 2010-11-29
Hi

I have just installed fedora 14 on my laptop with ubuntu (10.04 and natty) and win 7. Be aware, i had to reinstall grub as fedora installed its own boot loader that did not see my other os and then i had to update grub to get my original Grub2 bootloader to then see fedora.

It might have just been an option i missed when installing fedora.

EDIT: BTW its very blue. :)

Kind regards

---

### Post by Nickjpost on 2010-11-29
No, it's not something you missed. It did the same for me too. Are there instructions on how to get both to work, or should I just reinstall Ubuntu?

---

### Post by nm_geo on 2010-11-29
> **Nickjpost said:**
> No, it's not something you missed. It did the same for me too. Are there instructions on how to get both to work, or should I just reinstall Ubuntu?
 
You could do that but like Matt reinstalling Grub2 will work. Here is a good link to go by Fedora grub is anti-social with other distros. I would reinstall Grub2.
 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by nm_geo on 2010-11-29
> **matt_symes said:**
> Hi
 
I have just installed fedora 14 on my laptop with ubuntu (10.04 and natty) and win 7. Be aware, i had to reinstall grub as fedora installed its own boot loader that did not see my other os and then i had to update grub to get my original Grub2 bootloader to then see fedora.
 
It might have just been an option i missed when installing fedora.
 
EDIT: BTW its very blue. :)
 
Kind regards
 
I recently installed Fedora 14 on a laptop that has Ubuntu 10.04 and XP3, and in the F14 manual install mode there is an option to place the Fedora boot in it's own partition.  Then Grub2 will find F14 and all will be well.
 
I can't remember if I did that or not on my first install, but it seems like I deleted the Fedora partitions and started over on my 2nd install.  Anyway it is working now just fine.

---

### Post by matt_symes on 2010-11-29
Hi

> I recently installed Fedora 14 on a laptop that has Ubuntu 10.04 and  XP3, and in the F14 manual install mode there is an option to place the  Fedora boot in it's own partition.  Then Grub2 will find F14 and all  will be well.
 

Cheers. That's useful to know. I thought i must have missed something #-o.

Kind regards

---

