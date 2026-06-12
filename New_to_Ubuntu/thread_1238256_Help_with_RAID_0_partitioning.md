---
title: "Help with RAID 0 partitioning"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Rick Abraham on 2009-08-12
Hi guys well I have just done it and deleted Windows 7 from my laptop and what a feeling that was LOL
I have just decided to become a Ubuntu user and I like the look of it, over the years I have been a avid Mac user and can see many similar things between the two operating systems.
I have just downloaded Ubuntu 9.04 Alternate CD 64bit and want to install it on my laptop and start learning about Linux.
Im all excited.
BUT I require a little help understanding a few things.
I want to set up a Software based RAID 0 for performance I have 2x 500GB 7200 rpm drives in my laptop but the Linux partitions confuse me a little.
 
I believe that I dont require a swap partition due to I have 8GB of RAM and think that should do the job ok for all the applications I will be using.
Whats the go with the /root, /boot and /home partitions how do I set them up on the 2 drives and what size should I make each partition.
Im not going to worry about leaving any free space for NTFS partitions as Windows may go back on this PC but would be under a VMware virtual setup.
 
Any help would be great and or URL links to some great NEWBIE step by step guides.
Cheers Rick

---

### Post by Grannun on 2009-08-12
well first off, check to see if your motherboard supports hardware raid (which I assume it does since it has 2*500gb in it from the factory right?)  If it does, I beleive you set up the raid in the BIOS which makes life easier.  Second, you still need swap space since it is used for hibernation.

---

### Post by Rick Abraham on 2009-08-13
Actually my laptop does not have hardware RAID even though it was shipped with 2 hard drives strange isnt it.
I believe the 1737 model above mine had hardware RAID but they both use the same case etc.
So a software RAID 0 is my only option.
I am going to use the entire space of my hard drives for Ubuntu as Im sick of Windows issues.
I just am unsure of the partition sizes that I should have for /root, /boot and /home

---

### Post by Zack McCool on 2009-08-13
/boot is good at 150M.
/  (The root partition) depends on your needs.  I usually use 20GB and the remaining space for /home.

Also, as has been said previously, if you plan to hibernate, you should have a swap partition that's at least as big as RAM.

---

### Post by porchrat on 2009-08-13
> **Rick Abraham said:**
> Actually my laptop does not have hardware RAID even though it was shipped with 2 hard drives strange isnt it.
I believe the 1737 model above mine had hardware RAID but they both use the same case etc.
So a software RAID 0 is my only option.
I am going to use the entire space of my hard drives for Ubuntu as Im sick of Windows issues.
I just am unsure of the partition sizes that I should have for /root, /boot and /home

Honestly you are going to find a lot of conflicting opinions on the size of the various partitions. It all depends on what you are going to be doing with the machine as to how big you want your /home versus your root.

---

### Post by Rick Abraham on 2009-08-13
Thanks guys for all the info.
Have I got this correct all your program applications are stored in the /root partition and personal documents, music, videos etc is stored in your /home partition 
 
is this the basic way of looking at things

---

### Post by wizard10000 on 2009-08-13
Forgive me for straying OT but any system (and especially any RAID0 system) needs a *tested* backup strategy.

Statistically RAID0 doubles your chances for data loss.

---

### Post by Zack McCool on 2009-08-14
> **Rick Abraham said:**
> Thanks guys for all the info.
Have I got this correct all your program applications are stored in the /root partition and personal documents, music, videos etc is stored in your /home partition 
 
is this the basic way of looking at things

Not exactly.

Most applications are stored in the /usr branch.  If you do not have a separate partition for /usr, then yes, it will be a part of /.  Some applications will also install in /opt, but not that many, and if you don't have a separate partition for it, then it, again, is still a part of /.

Also, as stated above, using RAID0 increases your chances of a failure.  If one of the drives fails, everything is gone.  Be sure that you back up your data frequently, and test the backups.

---

