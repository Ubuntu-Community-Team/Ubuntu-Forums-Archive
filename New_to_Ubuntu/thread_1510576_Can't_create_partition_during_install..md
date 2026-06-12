---
title: "Can't create partition during install."
date: 2010-06-15
forum: New to Ubuntu
---

### Post by chedderslam on 2010-06-15
I am using an evga motherboard and utilizing it's onboard raid.  I have a raid 0 array for os, raid 5 for data.

I currently have windows 7 installed.

I am following the instruction here:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I have booted the live cd and tried to install after creating partitions.

I am getting the error:
the ext4 file system creation in partition #6 of serial ata raid isw_cbegeiieaa_Volume0 (stripe) failed.

What do I do?

---

### Post by ken631 on 2010-06-15
Bump
 
I wanna know this too?:p

---

### Post by john newbuntu on 2010-06-16
Because you are using fakeraid, the installation is slightly different.
When you get the point of manually partitioning your drive using the liveCD, on the gparted screen, go to the top right corner and choose the stripe device (something like /dev/mapper/...) and not /dev/sda or /dev/sdb.
Also, in the installer summary screen, click advanced and change the boot partition to /dev/mapper/... (the one which is striped).
For more details: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

