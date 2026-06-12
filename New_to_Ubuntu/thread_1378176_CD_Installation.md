---
title: "CD Installation?"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by richie3418 on 2010-01-11
If I downloaded the new version and put it on a cd how would you install it when you have a second partition? You can't boot from the cd because when it asks for the size of the partition you want it only shows the xp partition on the hard drive, it doesn't show that I already have Ubuntu on it. I was already told I can upgrade to the 10.4 LTS straight from my 8.04. I just wanted to know how to do it from a cd if I ever wanted to. I have searched a lot of threads and can't seem to find the right one. Can some one point me to the right how to?

---

### Post by slakkie on 2010-01-11
LTS to LTS is supported and can be done via the Alternate CD (for the how, please see the upgrade ubuntu link in my sig). 

Regarding the partitioning, dig a bit deeper and you should see/select your other disk as well.

---

### Post by Elfy on 2010-01-11
First - upgrading from a CD, use an alternate cd not a livecd. It will recognise where your partitions are and just upgrade.

Second - partitioning - if you ask it to do one of the automatic partition options then you will end up with 2 installs, the way to do this and to use existing partitions is to use the Manual Option - you can then specify which partitions will be overwritten (and formatted if you wish) and which will be used as they are (/home for example) and what mount points to use for each of your existing partitions.

---

### Post by 3rdalbum on 2010-01-11
For the upgrade, you burn the Alternate CD (not the regular desktop CD). Insert it while Ubuntu is running. There is a script called 'cdromupgrade'. Run this in a terminal. It will update the base system from the CD, and everything else from the Internet.

For your other problem, you need to 'Specify Partitions Manually' in the Ubuntu installer.

---

### Post by richie3418 on 2010-01-11
Thanks guys I hope I don't have to go the cd route but wanted to know. I am hoping to wait and do the LTS TO LTS upgrade.

---

