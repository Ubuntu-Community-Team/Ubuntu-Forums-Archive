---
title: "ran out of space the first day I installed ubuntu"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by jdrodrig on 2009-08-05
Hi,

I just installed 9.04 64bit next to a Vista installation and by mistake I just clicked away during the installation thinking that I would get an "average" or default installation.....but now I see that I have zero bytes left on my basic linux partition..... I even got an error message when trying to install upgrades (sudo-apt get upgrade) saying I had no space left...

what would be the best way to proceed?
1) try to resize the linux partition with gparted live, 
2) kill those partitions (the linux ext3, teh swap and the other) to have vista only, or
3) if I reinstall ubuntu on top of this, would I get the option to pick a larger size?

Thanks,
D.

---

### Post by c0mput3r_n3rD on 2009-08-05
> **jdrodrig said:**
> Hi,

I just installed 9.04 64bit next to a Vista installation and by mistake I just clicked away during the installation thinking that I would get an "average" or default installation.....but now I see that I have zero bytes left on my basic linux partition..... I even got an error message when trying to install upgrades (sudo-apt get upgrade) saying I had no space left...

what would be the best way to proceed?
1) try to resize the linux partition with gparted live, 
2) kill those partitions (the linux ext3, teh swap and the other) to have vista only, or
3) if I reinstall ubuntu on top of this, would I get the option to pick a larger size?

Thanks,
D.


Go to Applications -> Accessories -> Disk Usage Analyzer and check out how much space you have on your disk.

If you reinstall Ubuntu on top of the Ubuntu partition you will be able to resize the partition.  How big is your HDD?  How much space does Vista take up right now?  How much space did you allocate to Ubuntu?

---

### Post by XubuRoxMySox on 2009-08-05
Prob'ly the easiest way is to boot from the Ubuntu Live CD again, choose Install, and *manually* set up your partitions. Doing this will make a fresh install necessary, but it's not hard and it's a great way to learn.

You did not say how big your HD is, but since you are installing it alongside Windows, I recommend about 10 GB for root "/", twice your computer's RAM for "swap", and the rest of whatever is available (without messing up your Windows partition) as "/home".

---

### Post by lindsay7 on 2009-08-05
The first choice would be to repartition if you have space on your drive.  It is easy to do with Gparted.

---

### Post by 73ckn797 on 2009-08-05
See what space would be available to perform the resizing.

I would help to see what space has been alloted to each partition.

In terminal enter:
```
sudo fdisk -l
```

---

### Post by jdrodrig on 2009-08-05
thanks for all your answers, I am on my way home now to check on my desktop...the HDD is 640GB and it only has a basic vista installation (computer is 2 days old)....

---

### Post by esalnoj on 2009-08-05
As far as option 3, the installer will recognize ubuntu as already installed on a small partition, and want to install side by side with the existing ubuntu, unless you choose manual partitioning.

I have never resized partitions with gparted, just deleted and created. So no idea there as far as if your data will be lost on vista when resized.

I always delete the ubuntu partition from live CD gparted first, then install fresh. 

Hope this helps.

---

### Post by philinux on 2009-08-05
Open a terminal, Apps>Accessories>terminal

Use this.

```
df -h
```

Paste the results back here.

See this link too.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
You might have installed with a 2.5 gig system.

---

