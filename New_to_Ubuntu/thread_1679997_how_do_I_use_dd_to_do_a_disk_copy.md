---
title: "how do I use dd to do a disk copy?"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-02-01
Hi Ubuntu Community:

I accidentally removed all of my files from my home directory and the backup hard drive. A synopsis of that episode is found at: [http://ubuntuforums.org/showthread.php?t=1675564]("http://ubuntuforums.org/showthread.php?t=1675564")

I want to 
[LIST=1]
[*][COLOR="Red"]**make an identical copy of the hard drive that I accidentally hosed using dd**[/COLOR]
[/LIST]

Here is what I've done:

[LIST]
[*]I installed a 1Tb hard drive,
[*]booted from a live Ubuntu 10.04 CD
[*]used: sudo gparted, and
[*]saw that the 1 Tb drive is /devsda (with 931GiB),
[*]the old home drive that I hosed is /dev/sdb (232 GiB)
[/LIST]

The partitions of /dev/sdb are:
[LIST]
[*]/dev/sdb1 (230 GiB ext4)
[*]/dev/sdb2 (2.8 GiB extended), and
[*]/dev/sdb5 (2.8 GiB swap)
[/LIST]

I want to use dd to make a copy of the old drive.

Do I use:

**[COLOR="Red"]dd if=/dev/sdb of=/dev/sda[/COLOR]**

?

Also, do i need to install dd from the live CD?

Thanks,
Phil Smith
Duluth, GA

---

### Post by C.S.Cameron on 2011-02-01
Just open terminal and:

```
sudo dd if=/dev/sdb of=/dev/sda
```

No need to partition the new disk or anything.

---

### Post by kroq-gar78 on 2011-02-01
Correct me if I'm wrong, but considering that they're 2 different sized disks, wouldn't that somehow mess up the 2nd (1TB) disk?

---

### Post by YesWeCan on 2011-02-02
I think if your 1TB disk will appear to be a 250GB disk after the copy. It will also have the same UUID as the 250GB drive so it would be important not to try to boot with both drives connected.
Your data is in sdb1. So you could create a partition on the 1TB drive that is >=250GB and copy sdb1 to it using dd.

For more info about dd this is an excellent guide: [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by C.S.Cameron on 2011-02-02
> **kroq-gar78 said:**
> Correct me if I'm wrong, but considering that they're 2 different sized disks, wouldn't that somehow mess up the 2nd (1TB) disk?

After the dd, gparted can be used to expand the partition, or if a Windows o/s was on it, add another partition.

---

### Post by Old Jimma on 2011-02-02
Hi Community:

As a prelude to using sudo dd if=/dev/sdb of=/dev/sda I tried to mount /dev/sda first... and had a problem.

I tried to mount the 1Tb drive using:

sudo mkdir /media/MYNEWDRIVE
sudo mount /dev/sda /media/MYNEWDRIVE

and got the error message: you must specify the filesystem type

What do I need to do?

Thanks,
Phil Smith
Duluth, GA

---

### Post by YesWeCan on 2011-02-02
You will not be able to mount a drive that has no formatting. Mounting is not required for dd. It will copy using two unmounted disks.

Connect up both disks. Boot off live CD. In terminal type "sudo fdisk -l" and check what device paths have been assigned to each HD. In other words, make sure you know which disk is /dev/sda and which is /dev/sdb. If you get the of= wrong you'll be sorry! Then do "sudo dd if=/dev/sdx of=/dev/sdy bs=64k conv=notrunc,noerror" choosing the x and y appropriately.

This may take a while...an hour or more...and dd will give you no feedback at all while it does it. You'll see your HD light in a viscous blur, however.

---

### Post by Old Jimma on 2011-02-02
Hi YesWeCan:

Thanks for your explanation. dd is running right now.

I used

sudo dd if=/dev/sdb if=/dev/sda bs=64k conv=notruc,noerror

How will I know it worked correctly? I mean, will I get any sort of message or something?

Thanks!
PHil

---

### Post by psusi on 2011-02-02
It will return to the prompt when done, though you are kind of wasting your time.  What do you hope to accomplish by this?

---

### Post by Old Jimma on 2011-02-02
Hi YesWeCan:

Your dd code worked perfectly!  :p

Thanks!
Phil

---

### Post by Old Jimma on 2011-02-02
I've got one last question:

Suppose I want to restore the data that was on /dev/sdb that I archived on /dev/sda

will

sudo dd if=/dev/sda of=/dev/sdb 

work?

I wondered because /dev/sda is 1Tb and /dev/sdb is 250Gb

Thanks,
Phil

---

### Post by psusi on 2011-02-02
It will complain when it runs out of room on the destination, but if you are just moving back what came from there, it won't matter.

---

### Post by Old Jimma on 2011-02-03
psui:

I wiped out my hard drive and wanted to

1. make a backup on the wiped out hard drive, then

2. use photorec to extract jpgs from the wiped out drive.

I thought that I should make a backup of the wiped out drive first.

Does all of this seem like the way to go?

Thanks,
Phil Smith
Duluth, GA

---

### Post by psusi on 2011-02-03
I'm pretty sure that photorec does not modify the drive.  It just saves anything it finds somewhere else, so you don't want to duplicate the drive.

---

