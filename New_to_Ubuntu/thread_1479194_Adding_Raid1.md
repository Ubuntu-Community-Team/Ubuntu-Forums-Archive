---
title: "Adding Raid1"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Caveman2010 on 2010-05-10
Hello,
I have Ububtu 10.04 running in a box with a motherboard Asus M2A-MVP with an Athlon dual core 2200 MHz, 2 Gb of memory and a HDD Maxtor 120 GB 7200RPM.
I just got two new 750 GB HDDs and since the motherboard also has a RAID controller I would like to configure them as RAID1 and put in them a partition with /home.
Resuming, The fast 120 GB would have the system and the RAID1 array all the data.
Is this possible?
Have somebody done this?
I am new in the Linux world so I will appreciate any suggestions.
Thanks.

---

### Post by Gone fishing on 2010-05-10
Bad news your motherboards RAID controller is almost certainly a pseudo fake RAID controller for use with Windows and Windows drivers.

Good news Linux has excellent software RAID using mdadm basically the process is you partition the hard drive with RAID partitions and then and add the partions to the RAID  using mdadm then format as Ext3 what ever.

Opensuse this is a breeze in Ubuntu Hardy RAID 1 was a right pain in the *** with bugs and awful at least using raid on /, however, I think all the bugs are now fixed have a look at [http://superuser.com/questions/101630/creating-a-raid1-partition-with-mdadm-on-ubuntu](http://superuser.com/questions/101630/creating-a-raid1-partition-with-mdadm-on-ubuntu)

Now I hate to say this but...

install mdadm ```
sudo apt-get install mdadm
```

then open a terminal and look at the manual ```
man mdadm
```

I would suggest that you use the RAID on your /home partition rather than / but this is possible and I use RAID1 on / and /home on my server (Opensuse)

---

### Post by Caveman2010 on 2010-05-10
Thankyou "Gone fishing" for your fast replay. 
Searching this forum I found that 10.04 has big problems supporting RAID. I intalled 9.10 and everything is working as I wanted. 
It is hard to believe that I cannot use 10.04 in file servers.

---

### Post by Gone fishing on 2010-05-11
However, you probably want your server on an LTS 

I found this on howto get raid1 with lucid;

[http://ubuntuforums.org/showthread.php?t=1469169&highlight=raid1+lucid&page=2](http://ubuntuforums.org/showthread.php?t=1469169&highlight=raid1+lucid&page=2)

It looks like there was quite a lot of pain but a solution was found. I wonder whether putting /boot not on a raid partition and copying it onto both hard drives would work and might be easier?

---

