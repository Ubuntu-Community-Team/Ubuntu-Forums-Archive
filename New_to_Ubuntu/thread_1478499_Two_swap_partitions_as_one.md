---
title: "Two swap partitions as one?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by rufex2001 on 2010-05-09
I'd heard that it helps if the swap partition is as big as the ram available in the machine and found when installing the new 10.04 release that my swap partition is 2Gb when I have 4Gb RAM. Now, while this may or may not be true and more swap space may or may not help the system performance (feel free to answer this question too), the question that I have here is: Do two partitions of 2Gb each act as one of 4Gb? Because that is what I did when installing, I reduced the size of another partition and made the new and free 2Gb a new swap partition, so now there's two...

Thanks in advance! 

A big Ubuntu fan!

---

### Post by utnubuuser on 2010-05-09
I think 2 separate partitions only helps if they're on seperate disks.

The equal amounts swap/ram is a hibernate issue - I think the safe formula was 1.5x ram.
With 4gigs of ram, I'd be surprised it your swap ever gets used at all...

---

### Post by jbrown96 on 2010-05-09
You don't need swap at all with that much ram.

---

### Post by cariboo on 2010-05-09
I only use one swap partition for two installs. 2gb is more than enough unless you hibernate your system, them I'd go with twice the ram.

---

### Post by rufex2001 on 2010-05-10
Thank you all for the responses! I don't really hibernate that much, although there is the occasional hibernation. I'm glad to see that with that much RAM, this should not really be a concern. However and with the ultimate purpose of learning, the question still stands.

Say I decide one day to hibernate me **** off and the system finds itself in need of more that the 2Gb that are offered in one of the swap partitions. Will it look for, see and find another 2Gb swap partition and proceed to use it, or will it ignore it, since it only uses continuous space as swap?

I take it the short answer is NO, but still... anyone?

Either way, thank you very much! Long live GTK+, Ubuntu and Gnome!

---

### Post by narendraD on 2010-05-11
> **rufex2001 said:**
> Thank you all for the responses! I don't really hibernate that much, although there is the occasional hibernation. I'm glad to see that with that much RAM, this should not really be a concern. However and with the ultimate purpose of learning, the question still stands.

Say I decide one day to hibernate me **** off and the system finds itself in need of more that the 2Gb that are offered in one of the swap partitions. Will it look for, see and find another 2Gb swap partition and proceed to use it, or will it ignore it, since it only uses continuous space as swap?

I take it the short answer is NO, but still... anyone?

Either way, thank you very much! Long live GTK+, Ubuntu and Gnome!

With 4GB of RAM you may not need a swap at all. Even if you did hibernate at some point, you may not need 4GB of RAM and even if the system is in need of more than the 2GB of swap, i do not think it will look for another swap partition on the same or different hard disk. The swap partition is coded in the fstab and i do not think 2 swaps are possible.

---

### Post by perham on 2010-05-11
> **rufex2001 said:**
> I'd heard that it helps if the swap partition is as big as the ram available in the machine and found when installing the new 10.04 release that my swap partition is 2Gb when I have 4Gb RAM. Now, while this may or may not be true and more swap space may or may not help the system performance (feel free to answer this question too), the question that I have here is: Do two partitions of 2Gb each act as one of 4Gb? Because that is what I did when installing, I reduced the size of another partition and made the new and free 2Gb a new swap partition, so now there's two...

Thanks in advance! 

A big Ubuntu fan!

you can have as much as swap as you want and system uses them all (if you mount them). as for hibernation, I have never tried using two swaps and see if it works, but, technically it should. you can also prioritize your swaps. check "man swapon" for more info.

---

### Post by QLee on 2010-05-11
[QUOTE=rufex2001]I'd heard that it helps if the swap partition is as big as the ram available in the machine and found when installing the new 10.04 release that my swap partition is 2Gb when I have 4Gb RAM. Now, while this may or may not be true and more swap space may or may not help the system performance (feel free to answer this question too), ...[/QUOTE]

With 4G RAM you probably don't hit swap so increasing the size of swap is unlikely to give a well working system any performance increase.

In order to hibernate, the system has to write the contents of RAM to your swap. Since compression is used, setting the swap equal to the amount of RAM is recommended for hibernation (add a hundred meg or so if you want). The old "rule" of double RAM is left over from the days when RAM was expensive and almost all systems were low on RAM and needed to swap a lot. 


[QUOTE=rufex2001] ...the question that I have here is: Do two partitions of 2Gb each act as one of 4Gb? Because that is what I did when installing, I reduced the size of another partition and made the new and free 2Gb a new swap partition, so now there's two...
[/QUOTE]

Yes, they can.

You need to enter both of them in your fstab so they will be mounted as your swap at boot time. After you edit the fstab (make sure they are not optioned "noauto"), issue the command sudo swapon -a, that will give you the full swap immediately.

---

