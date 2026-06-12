---
title: "New to Ubuntu - very pleased, but HD might be a mess"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by JPP4 on 2010-08-17
[SIZE=3]Hello to all - got turned on to Ubuntu and now on both laptops Dell mini 9 and Inspirion 1521:D Like Linux much better than MS.

Not a real experienced computer user, but enjoy learning. Problem is I think I got too many partitions on my hard drive. The 1521's got Vista and Ubuntu dual booted. Tried to erase?format? a partition that said "XP embedded" remember trying to load XP long time ago so tried to remove it.

When I erased it, Ubuntu wouldn't boot and got a Grub error so I ran LiveCD and reinstalled. Now 2 Ubuntu's are on the disk. Tried to read a little and installed gpart. Included a screenshot of disk, sorry not good with posting system info and knowing my way around yet. How can I clean this up? or is there a good resource for learning how to do so? 

Many thanks 




[/SIZE]

---

### Post by elliotn on 2010-08-17
Welcome to the forum, well your screenshot shows dat u have 2 ext4 partition and 2 ntfs partition,
U need to figure out which partion holds your prefered installation of ubuntu, then wipe other, I suggest u erase all those ext4 partitions and all unallocated space then reinstall ubuntu again, i know its pain but it would help to get rid of your plenty partition

---

### Post by JPP4 on 2010-08-17
> **elliotn said:**
> Welcome to the forum, well your screenshot shows dat u have 2 ext4 partition and 2 ntfs partition,
U need to figure out which partion holds your prefered installation of ubuntu, then wipe other, I suggest u erase all those ext4 partitions and all unallocated space then reinstall ubuntu again, i know its pain but it would help to get rid of your plenty partition

Thank you for the reply and welcome. So I erase the 2 ext4 partitions. Do I erase the 2 linux swap partitions as well and the reinstall ubuntu? Many thanks again

---

### Post by silverglade00 on 2010-08-17
Yes, it would be best to remove them both and reinstall.

You want to get rid of /dev/sda4 and higher. Keep sda1, sda2, and sda3. Those are your Windows and recovery partitions.

If you feel confident working with partitions, you might want to use 3 for Ubuntu. One for swap, one for / and one for /home. The one for /home will hold all of your user files and makes it easier to reinstall later on if you wish. These will have to go into an extended partition.

---

### Post by JPP4 on 2010-08-17
Thanks! Up running again. JP

---

