---
title: "boot partitioning how much space needed?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by 007casper on 2008-12-29
I want to partition the hard drive as described here
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

however, it doesnt have any information on boot partition if there is a minimum space requirement.  

Is 100mb space for boot partition decent?

I have a 500GB hard drive with 1Gb ram... no xp, vista... only ubuntu

I was going to split as 

20GB -- ubuntu/(ext3)
477GB -- ubuntu/home(ext3)
2GB -- swap
100Mb -- boot ???

---

### Post by dk21 on 2008-12-29
You don't need a boot partition...

You will need only a \, a Swap and a \home partition for a good configuration...

---

### Post by blueridgedog on 2008-12-29
A separate /boot is a hold over from the days when you needed the kernel in the first so many sectors of larger disks.  As mentioned / swap and /home work great.

---

### Post by 007casper on 2008-12-29
#1 primary 20.0GB f ext3 /
#3 primary 477.2GB f ext /home
#5 logical 2.9GB F swap swap

should I pick Primary over Logical when I am partitioning the platform? /

what is the difference?

thank you.

---

### Post by 007casper on 2008-12-30
bump

---

### Post by Partyboi2 on 2008-12-30
You can only have 4 primary partitions so if you plan to have more then 4 partitions on the hard drive make a extended partition that way you can have plenty more partitions.

---

### Post by logos34 on 2008-12-30
> **007casper said:**
> 
should I pick Primary over Logical when I am partitioning the platform? /

what is the difference?


+1 Partyboi's comments

primary or logical for /, doesn't matter to linux

---

### Post by hyper_ch on 2008-12-30
and a seperate boot partition is needed if you want to fully encrypt your system. If not, then you don't really need one.

---

### Post by 007casper on 2008-12-30
thanks everyone... 

~fully encrypt the system with boot partition...
I know what encrypt does... how does an encryption works on a platform ?? 
will you please elaborate?

---

### Post by hyper_ch on 2008-12-30
use the alternate install cd, there you have an option to fully encrypt the system. However

(1) reading/writing from an encrypted system is significantly slower... during normal operation you won't notice much

(2) also be sure to make regular backups - if the encrypted container fails there's no viable option of recovering your data.

---

