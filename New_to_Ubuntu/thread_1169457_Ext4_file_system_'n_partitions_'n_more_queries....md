---
title: "Ext4 file system 'n partitions 'n more queries..."
date: 2009-05-25
forum: New to Ubuntu
---

### Post by melrokz on 2009-05-25
1. What is the improvement over ext3 that ext4 has?

2. Why do we make a (i) /home or (ii) /boot partition?

3. Will a /home partition get formatted on reinstall of Ubuntu into the root partition?

4. Can we add more ext4 partitions with our own mount points?
   Eg: /mel

5. Can you suggest a good software that runs from a boot cd which can backup and restore ext4 partitions?

---

### Post by Sef on 2009-05-25
1) Ext 4 is faster.

2) Home partition is for keeping your data off of your os partition (root.)  
A boot parition is not needed for Jaunty.  Some people like to separate the boot partition from the root partition.

3) Yes, I have my root (jaunty) and my home on ext 4.

4) not offhand. Would need to do some research on that.

5) Read [Ext 3 and 4 - Which file system to install?]("http://ubuntuforums.org/showthread.php?t=1133719")

---

### Post by melrokz on 2009-05-25
Thanks, sef. One more thing. My ubuntu 9.04 installs only in safe graphics mode. Is it because I have an outdated video card? (Intel 845GL chipset)

---

### Post by yaroto98 on 2009-05-25
4) I don't see any reason why it wouldn't be possible. When you install Jaunty the partition editor can make as many partitions as you want. Any or all of them can be ext4. For boot Jaunty will want a /swap and a /root partition, but you can create your own /home and more. Even if you've already installed, you can just use gparted to make more partitions, and just add it to your /etc/fstab for auto mounting on boot.

---

### Post by presence1960 on 2009-05-25
3. If you have a separate/home partition it will not get formatted on reinstall if you do this. At the partitioner screen of the install choose "manual" option. Set the root partition to install Ubuntu onto, then highlight the /home partition and click Edit. Set the mountpoint to /home. **Make sure the format box is UNCHECKED or it will be formatted** This will save all data on your separate /home partition and it will mount automatically as home for you when you use Ubuntu.

---

