---
title: "Setup of Software RAID0 using Ubuntu 10.10 Alternate CD"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by jr_herman on 2010-12-11
I’m trying to set a Software RAID0 using the Ubuntu 10.10 Alternate CD. I’m using 2 500 GB HDD. I used this guide to install it. [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I don’t think its all the way updated to 10.10. But I gave it a shot any way. I’m running into a problem at the Partition disk menu. Looks like RAID0 device is set up to me.(picture of screen attached). On the free space of the RAID device I press enter and automatically partition the free space. I try to move on with the results. I the prompt ask if I want to write the changes to the disk I pick yes. (pic attached). It starts to create the ext4 file system for / in RAID0 device. 

A failure prompt states that the attempt to mount a file system with swap in RAID0p5 device # at none failed.

I’m lost.](*,) Should partition 5 (logical) on the RAID0 be set as something different than swap?

---

