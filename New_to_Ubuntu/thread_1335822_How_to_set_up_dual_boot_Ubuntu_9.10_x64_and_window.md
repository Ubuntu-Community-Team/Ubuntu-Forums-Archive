---
title: "How to set up dual boot Ubuntu 9.10 x64 and windows XP"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by tafbuntu on 2009-11-23
I have tried installing xp first and allocating only 50gb of 500gb partition for NTFS but when installing the .910 the partion manager (forgot the name sorry) sees the whole hdd as free. 
 
I have tried to install Ubuntu first and XP doesn't see the Ubuntu OS either. Help.
I am a real beginner but can follow directions.

---

### Post by ranch hand on 2009-11-23
You will have an easier time if you install Win JerryLewis Pro first.  MS just works better that way.

After you have that done boot tro the Live CD and pull up gparted from System>Administration>Partition Editor.

You should see your MS partition there.  Make your other partitions for 9.10 from there.  You need a swap partition (1Gb) and I would use 2 partitions for your installation a / (root) partition and a /home partition.  Make your root partition about 20 to 25Gb and leave the rest for your /home.   Write down the partition number for / and /home.

Close gparted and make sure that there are no mounted partitions, they should show on your desktop.  If they are there, right click on them and then click on "unmount".

Start your installer from the desktop.  When you get to the partitioner, choose the "manual" option.

You can then select the partitions you set up for / and /home by right clicking on them and clicking on "change".  Take your time and follow directions.  You can do this.

Have FUN.

Post back if you have more questions.

---

### Post by plusnplus on 2009-11-24
Hi tafbuntu,

Better install XP first.
when you do partition, 450gb xp and  50gb ubuntu, don't format the 50gb as ntfs. Leave it as unformat.
ubuntu installation should can see the unformat 50gb partition and suggest it as side by side instalation.

---

