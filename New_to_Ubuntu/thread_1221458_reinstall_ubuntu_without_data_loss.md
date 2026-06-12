---
title: "reinstall ubuntu without data loss"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by mr_cardholder on 2009-07-23
Hey guys,
Been a while since I had to post but I ran into a major problem recently. I had my ubuntu system configured to run as a webserver. I had to do a major update (long unrelated story). In the process I managed to mess up my ubuntu installation something fierce. I can only boot into command line and some other programs, like NFS, have completely stopped working. I am thinking the only way to fix this is to reinstall the os but I have a LOT of valuable data on this server (about 500 GB) which I really cannot afford to lose. So I am curious if there is a way to reinstall only the operating system. If anyone has any better suggestions, I am certainly willing to listen.

Thanks,
mr_cardholder

---

### Post by sydbat on 2009-07-23
If your /home (data) is in a separate partition from / (root), you should be able to reinstall no problem.

If / and /home are in the same partition, and you have the room, create a new partition and move /home (data) into it and reinstall.

---

### Post by mr_cardholder on 2009-07-23
> **sydbat said:**
> If your /home (data) is in a separate partition from / (root), you should be able to reinstall no problem.

If / and /home are in the same partition, and you have the room, create a new partition and move /home (data) into it and reinstall.

You may have to give me some more direction on this. I'm still pretty novice at moving partitions around. I believe / and /home are in the same partition as I just followed the standard install procedure. I should also mention that the data I need is in /storage which is a self created folder with 777 perms.

---

### Post by sydbat on 2009-07-23
> **mr_cardholder said:**
> You may have to give me some more direction on this. I'm still pretty novice at moving partitions around. I believe / and /home are in the same partition as I just followed the standard install procedure. I should also mention that the data I need is in /storage which is a self created folder with 777 perms.K.

Use the Live CD and go into the partition editor (System > Administration > Partition Editor) and see if your /home is in a separate partition (it will be listed as such if it is). 

If not, see how much empty space you have and if you can create a new partition that will be big enough to move your 'storage' folder into.

Alternately, if you can, try an external hard drive to put your data onto temporarily and then reinstall accordingly...this time making separate partitions for / and /home.

---

### Post by mr_cardholder on 2009-07-23
> **sydbat said:**
> K.

Use the Live CD and go into the partition editor (System > Administration > Partition Editor) and see if your /home is in a separate partition (it will be listed as such if it is). 

If not, see how much empty space you have and if you can create a new partition that will be big enough to move your 'storage' folder into.

Alternately, if you can, try an external hard drive to put your data onto temporarily and then reinstall accordingly...this time making separate partitions for / and /home.

That might be the best way to go. I already have a 500 GB external that has some of the really important data on it already. I will move everything else I can onto it and then repartition it using the live cd.

---

### Post by mr_cardholder on 2009-07-23
> **mr_cardholder said:**
> That might be the best way to go. I already have a 500 GB external that has some of the really important data on it already. I will move everything else I can onto it and then repartition it using the live cd.

Actually, now that I have looked through the system some more, it looks like it may only be necessary to reinstall the gui. Most of the important programs seem to be intact. Is there a way to just install the gui on the old partition?

---

### Post by oldfred on 2009-07-23
This should install kde
 sudo apt-get install kubuntu-desktop

---

### Post by Paddy Landau on 2009-07-24
Also see [how to move home into its own partition]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/").

---

### Post by LookTJ on 2009-07-24
While the above replies is all good.

if you plan on putting /home into its own partition.

There are some to point out here

1.  The install GUI in 9.04 when manual partitioning setup is in process, therefore go the alternate install path.(I tried this, and apparently ubiquity has presented me with a ugly bug, so I decided to use a different distro that I like)

2.  Would recommend to use 8.10 if you aren't comfortable with the command line interface yet.

Hope this gives some insight :)

---

### Post by mr_cardholder on 2009-07-24
Thanks for all the advice everyone. It looks like I will have to do a reinstall since it seems too much stuff is offline after reinstalling the desktop.

---

### Post by ugm6hr on 2009-07-24
Remember that moving, resizing and creating partitions can cause data loss too.

If the data is important, I would strongly recommend making a backup first.

If you don't have the necessary storage to do this, get some before risking your data.

---

