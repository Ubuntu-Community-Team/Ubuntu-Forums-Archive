---
title: "partition not writable"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-24
Hi, I have a common /data partition for both ubuntu and debian with ext4 filesystem. The partition doesn't allow me to write to. It has the following permission
drwxr_xr_x root root /data
So I changed the owner of the partition to sid using 
sudo chown -R sid:sid /data
Then I was able to write to the partition . My question is how do I make the partition writable right from boot time onwards. Please help

---

### Post by bodhi.zazen on 2010-05-24
> **oaridus said:**
> Hi, I have a common /data partition for both ubuntu and debian with ext4 filesystem. The partition doesn't allow me to write to. It has the following permission
drwxr_xr_x root root /data
So I changed the owner of the partition to sid using 
sudo chown -R sid:sid /data
Then I was able to write to the partition . My question is how do I make the partition writable right from boot time onwards. Please help

You should now be good to go.

For details see : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

But the "bottom line" - You should only need to run that command once.

---

### Post by oaridus on 2010-05-25
Thanks Bodhi for the great tutorial. Ya, now after again booting into my system the /data partition is writable. It has the following permission
drwxr_xr_x sid sid /data

Also I changed the mount point to /media/data. So that /data appears in my Places menu for easy access. It appeared a "11GB file system". Then I used tune2fs to label the partition
tune2fs -L Data /dev/sda7 
and now on boot up I have the Data in the Places menu. Thanks once again.

---

