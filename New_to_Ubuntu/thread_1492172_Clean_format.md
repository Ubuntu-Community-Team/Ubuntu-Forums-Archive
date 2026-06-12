---
title: "Clean format"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by J4M13N on 2010-05-24
Hey,
I have ubuntu 10.04 but I want to do a clean format of my hard drive and reinstall 10.04, I know how to do it in XP but how do I go about doing this in ubuntu?

Thanks.

---

### Post by oldfred on 2010-05-24
You can just use the install choice of use entire hard drive. That will give you just / (root) and swap.

But do you plan extra partitions like /home or data? If so you have to use manual install so you can set up extra partitions.  I like to plan partitions in advance and set them up with gparted. Then use manual install to choose the partitions I previous set up. You can do it as part of the install, I just do it first.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by J4M13N on 2010-05-24
I don't want to partition or anything like that, I have one partition which is my entire HDD. Can I insert the Ubuntu 10.04 CD and reinstall from that?

---

### Post by roger_1960 on 2010-05-24
Yes

As oldfred said, install from Live CD using the "use entire drive" option.  Note that this will erase everything including any data.

---

