---
title: "Unmounting and partitioning"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by jenova_skill on 2009-05-06
Im trying to create a new partition and I'm having a few problems.
1st off I installed Kubuntu on it's own partition ( small 5.5gigs) just to test it out. I took off kubuntu and now i have a 5 gig partition witch i deleted and now it's just unallocated space.

Im running Gparted 

I have  
   /dev/sda1   ext3    /      
   unallocated                

There is no options to resize or make new partition with dev/sda1
I assume i need to unmountit.......
Using gparted it won't let me unmounted says something about probably a partition attached to it  and I'd have to do it manually. 

How do i unmounted it manually and will this enable me to resize it?
I want to make my drive basicly split in half... 
At the moment it's  143gig and  5.5 unallocated.

---

### Post by jenova_skill on 2009-05-06
I Ran a live Cd and tried to do the same thing and presto it works 100%..... I suppose due to my trying to change the Partition I am using it won't work.

---

### Post by Didius Falco on 2009-05-06
> **jenova_skill said:**
> Im trying to create a new partition and I'm having a few problems.
1st off I installed Kubuntu on it's own partition ( small 5.5gigs) just to test it out. I took off kubuntu and now i have a 5 gig partition witch i deleted and now it's just unallocated space.

Im running Gparted 

I have  
   /dev/sda1   ext3    /      
   unallocated                

There is no options to resize or make new partition with dev/sda1
I assume i need to unmountit.......
Using gparted it won't let me unmounted says something about probably a partition attached to it  and I'd have to do it manually. 

How do i unmounted it manually and will this enable me to resize it?
I want to make my drive basicly split in half... 
At the moment it's  143gig and  5.5 unallocated.

Are you running Gparted from your hard drive? If that is the case, it won't let you resize the partition because that is the running Ubuntu partition.

To resize that partition, you need to boot with the Live CD and do it from there. When you open Gparted it should then allow you to resize and create new partitions. If is still won't let you, look on the left side of the Gparted screen and see if you see any key icons.

If you do, highlight that partition, right-click and unmount it. This shouldn't be the case though - I've never had a partition mounted when I run the Live CD unless I mounted it myself.

I hope this helps...

Regards,

Didius

---

