---
title: "Partition questions"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Amockineuropa on 2009-11-19
I have installed on my laptop Windows Vista and Ubuntu. Question lies in HOW I partitioned my hard drve.
 It is laid out as thus;
160 GB HD 
PQService 11GB (NTFS) /dev/sda1
Windows    75GB (NTFS)/dev/sda2
Extended   75GB /dev/sda3 (contains logical partition)
      Ubuntu 68Gb Ext3 (Version 1.0) /dev/sda5
       Swap space 7.9Gb /dev/sda6

As you can see it seems that I have loaded Ubuntu within the area titled EXTENDED! Now the system seems to work just fine only little thing that bothers me is at BOOT up screen. It list Ubuntu 3 TIMES and they all appear to be copies as if I installed the program 3 times. Windows is listed only once. Is this set up correct? If not is there a way to delete the EXTENDED shell while still keeping my Ubuntu info?

---

### Post by SuperSonic4 on 2009-11-19
> **Amockineuropa said:**
> I have installed on my laptop Windows Vista and Ubuntu. Question lies in HOW I partitioned my hard drve.
 It is laid out as thus;
160 GB HD 
PQService 11GB (NTFS) /dev/sda1
Windows    75GB (NTFS)/dev/sda2
Extended   75GB /dev/sda3 (contains logical partition)
      Ubuntu 68Gb Ext3 (Version 1.0) /dev/sda5
       Swap space 7.9Gb /dev/sda6

As you can see it seems that I have loaded Ubuntu within the area titled EXTENDED! Now the system seems to work just fine only little thing that bothers me is at BOOT up screen. It list Ubuntu 3 TIMES and they all appear to be copies as if I installed the program 3 times. Windows is listed only once. Is this set up correct? If not is there a way to delete the EXTENDED shell while still keeping my Ubuntu info?

I'd be more concerned about your figures. Please share your secret how to get more space :popcorn:

IIRC the default listing is Ubuntu, Ubuntu Recovery and Memtest

What version of ubuntu do you have? If it's not Karmic can you post the output of ```
cat /boot/grub/menu.lst
```

if it is Karmic I cannot help

---

### Post by Matt__ on 2009-11-19
The multiple listings for Ubuntu will probably be the different kernel versions after you have updated it and can be removed (try ubuntu tweak) and the ubuntu partition may be listed as logical because you have so many other parts already on that drive (think the limit is 4 parts, then you have to use logical)

// edit, the extended part is made up from both your swap and ubuntu partition (youre not actually getting another 75Gb :D )

---

### Post by bodhi.zazen on 2009-11-19
That all sounds normal.

for information on partitions see : 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

In terms of listing of Ubuntu, ubuntu gest two listings for each kernel.

One listing is "normal", one listing is "recovery mode" and is used if you are having problems, and one listing is mem test, again to check your RAM if you are having problems.

---

### Post by marcopolo1981 on 2009-11-19
You can't delete the extended partition without removing Ubuntu.
I have never had any problems with having Ubuntu in an extended partition.

Mark

---

### Post by Amockineuropa on 2009-11-19
Yes I recently upgraded to 9.10 (Karmic Koala) That figure you beside the EXTENDED is 75Gb and it includes the Ubuntu (68Gb) and the Swap parts(7.9Gb). I think I somehow installed it wrong it looks like a put a book into another box here. It works but still. I wish I had done it correct the first time. Does this look correct of did I mess up?

---

### Post by marcopolo1981 on 2009-11-19
Please open a terminal and type:

```
cat /boot/grub/grub.cfg
```

Then post the output here.

Your hard drive configuration looks fine, so lets see if we can make sure that your boot configuration is correct.
I suspect that bodhi.zazen is correct, but lets make sure.

---

### Post by louieb on 2009-11-19
> **Amockineuropa said:**
> ...Does this look correct of did I mess up?

Nothing wrong with using an **extended** partition. Having one gives you the flexibility to have more that 4 partitions.  BTW: the partitions inside the **extended **partition are called **logical** partitions.  

You have good and simple partition setup.  If you want you could shrink your Ubuntu partition (10-20GB is what I use)  and use the space for a separate data partition or a partition to mount /home. (or both)  How you partition  the space is really up to you.

---

