---
title: "Confused with output of DiskUsageAnlyser,DiskUtility and 'df' cmd"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by ramujinius on 2010-12-06
Confused with output of Disk Usage Anlayser, DiskUtility and 'df' cmd. Each application is giving different answer for free space and disk capacity.

Disk usage analyzer says
Capacity : 80.4 GB
Available : 75 GB

"df -h"  says
Capacity : 81 GB
Available : 72 GB

Disk Utility says
Capacity : 88 GB

I am not sure which output is right and which one is wrong

Could someone let me know wat is the issue? Nearly 14 GB of free space is missing.

Actually its 90 GB capacity disk which includes 1.8 swap memory 

Attached the screen shot of all output

---

### Post by TeoBigusGeekus on 2010-12-06
Try
```
df -H
```

---

### Post by mikechant on 2010-12-06
Firstly, the 88Gb figure given by Disk Utility is the size of the partition - unformatted. Formating the partition brings the space available when the filesystem is empty down to about 81Gb, which is about what df and usage analyser say.

Secondly, the difference between the 72Gb and 75Gb 'available' figures probably relates to the fact that 5% of the space is reserved for the superuser by default, one of the figures includes the 5% and the other does not.

So all the numbers are correct, they are just measuring different things!

The 10% formatting overhead is something you can't easily get round (you could mess around with the ext4 formatting parameters or use a different type of filesystem with less overhead but this could be complicated or inconveinient).

The 5% reserved space for the superuser is intended to let the system keep running in the event of one of the users filling up all avaiable space. You may want to reduce this reserved area or eliminate it altogether. This is quite easy.
For example, to reduce the reserved space from 5% to 1%, open a terminal and type:
```
sudo tune2fs -m 1 /dev/sda6
```
then do
```
df -h
```
again and you should see the result.

I've done this several times without any problems.
I'd recommend leaving 1% reserved on root partitions and 0% on data partitions.

---

### Post by asmoore82 on 2010-12-06
Firstly, there is the mathematical "skew" because humans count in multiples of 1000,
but binary machines count in multiples of 1024 (powers of 2).

So 90 Human GB is 90 * 1000 * 1000 * 1000 = 90000000000 bytes.

This is 90000000000 / 1024 / 1024 / 1024 = 83.82 real machine GB.

Secondly, see "Firstly" in previous post :D.

Next, Linux systems by default reserve some space.
While technically free space, it is **not** available to standard user accounts,
so some of the more user oriented tools go ahead and subtract this for you.

To see how many blocks are reserved, use tune2fs:
```
sudo tune2fs -l /dev/sda6 | grep -i reserve
```

To change it, use `-m` as a whole percentage:
```
#reserve 5%
sudo tune2fs -m 5 /dev/sda6

#reserve 0%, get the most free space possible
sudo tune2fs -m 0 /dev/sda6
```

I always leave space reserved on my OS partitions but leave 0% on my /home partition.

---

