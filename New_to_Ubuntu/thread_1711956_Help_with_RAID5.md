---
title: "Help with RAID5"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by lindb310 on 2011-03-22
Hello everyone,

We have a failing RAID5 array on our backup server, if anyone knows  anything useful about RAID5 we would really appreciate your help. Our  goal is preserve as much of the data as possible.

Here is some relevant information:

We have 4 drives in the raid array, sda1, sdb1, sdc1, and sdd1. 

"mdadm --examine /dev/sda1" tells us that sdb1 is faulty removed
"mdadm --examine /dev/sdb1" tells us that all drives are fine
"mdadm --examine /dev/sdc1" tells us that sda1 is removed and sdb1 is faulty removed
"mdadm --examine /dev/sdc1" tells us that sda1 is removed and sdb1 is faulty removed

Filesystem checks on md0 yells about an invalid superblock reference,  and the device /dev/md0 alternates between active and inactive in  unpredictable ways. 

Any suggestions?

---

### Post by deconstrained on 2011-03-22
Since you're running filesystem checks on the device I assume it's already experiencing downtime (running a check on a mounted filesystem is very dangerous as you know). So shutting down the machine is not much more of a problem, correct?

First look at /proc/mdstat to verify that the information there reflects the problem you're experiencing -- namely, /dev/sdb1 not responding, has a corrupted superblock, is physically dead, etc.

Then you need to mark the drive as failed: 
mdadm --manage /dev/md0 --fail /dev/sdb1

Then remove the drive from the array:
mdadm --manage /dev/md0 --remove /dev/sdb1

Then power down (or, if your motherboard's firmware and your chassis hardware permits, you can hot-swap it out). If the drive can indeed be diagnosed as physically failed, replace it with a new drive and put the same partition map on the new drive as the old one had (or at the very least make a partition that's the same number of sectors for use in the array). Once you have a functioning drive with a similar partition for use in the array, you'll need to add the new partition to the array (the new /dev/sdb1) and it will begin the self-healing process;

mdadm --manage /dev/md0 --add /dev/sdb1

Its progress will be displayed in /proc/mdstat; use the 'watch' command (i.e. watch /proc/mdstat) to view it working continuously.

Sources:
The manual page ('man mdadm')
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)
[http://www.linuxquestions.org/questions/linux-server-73/mdadm-raid-5-single-drive-failure-644325/](http://www.linuxquestions.org/questions/linux-server-73/mdadm-raid-5-single-drive-failure-644325/)

---

