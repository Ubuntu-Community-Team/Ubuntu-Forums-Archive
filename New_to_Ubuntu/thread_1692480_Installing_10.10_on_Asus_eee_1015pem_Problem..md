---
title: "Installing 10.10 on Asus eee 1015pem Problem."
date: 2011-02-21
forum: New to Ubuntu
---

### Post by StarZtorm on 2011-02-21
First time user on both forum and operative system here. 

So i wanted to install Ubuntu, after having a couple of tries from the USB drive i was kinda fascinated with the system.

So i selected the option to install (right after boot) and was waiting to follow the step by step guide from the sites download pages. 

the option to install alongside OS isnt there!

After doing some googling i concluded this had to do with the HDD on the netbook. There are already 4 partitions on the HDD.

So, now im left with the choices to either erase disc or specify partitions manually. Erase disc im guessing means erasing the whole HDD, partitions and everything. If i do that im gonna lose windows and recovery :S Cant do that.

So im left with specifying partitions.. The D: partition would be fine to use. (in windows its empty) but what filesystem do i format to? is there a step to step guide for this?

---

### Post by StarZtorm on 2011-02-21
Bump

---

### Post by maqtanim on 2011-02-21
You need to select the "specify partitions manually" option.

In the next step, in the partition table the D drive should be labeled as sda5. Make sure whether the total space of D drive is same as the sda5 drive.

Select the ext4 format for the drive and select the mount point as "/".

Then proceed for the next steps.

******************************************************************

may be this link will help you
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by StarZtorm on 2011-02-21
Thank you!

---

