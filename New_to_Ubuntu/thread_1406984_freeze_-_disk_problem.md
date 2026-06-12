---
title: "freeze - disk problem?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by ubnewb1 on 2010-02-14
I am having a problem where one of my disks (sda) in a software raid has a solid red light and the computer freezes, goes very slow, for about 2-3 minutes. It happens quite often but not on a regular basis (doesn't appear to be a pattern).
  
I am using Ubuntu 9.10 and I have 3 Western Digital WD15EADS-00P8B0 disks set up as follows
  
/dev/sda1   1 Gig 
/dev/sda2   1.4T
/dev/sdb1   1 Gig 
/dev/sdb2   1.4T
/dev/sdc1   1 Gig 
/dev/sdc2   1.4T

I am using Raid 
Raid 1 /dev/md0 /sda1,/sdb1,sdc1 - Boot
Raid 5 /dev/md1 /sda2,/sdb2,sdc2

Then LVM2
PV /dev/md1
LV /dev/VG/swap 5Gig
LV /dev/VG/root 20Gig
LV /dev/VG/home 2.64T

I have disabled WDIDLE3, not changed TLER (although not sure you can on these disks)

Raid is in sync whenever I look at them.I have run two extended smartctl tests on /dev/sda and there are no problems.

I have moved /dev/sda to another slot and still get the problem
Logs - nothing appears to be at the same time.

saidar - doesn't appear to show anything at the time it is happening.

htop - doesn't show anything from a process, cpu, memory perspective when it is happening

I have exhausted my very limited knowledge - any help would be much appreciated :)

Regards

---

