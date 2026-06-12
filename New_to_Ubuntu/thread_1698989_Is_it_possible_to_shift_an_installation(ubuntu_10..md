---
title: "Is it possible to shift an installation(ubuntu 10.10)?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-03-03
Hi, have been using Ubuntu 10.10 (newbie to linux) for a while and loving it. The mistake I made was just allotted 10 gb for the installation ( no expansion possible as Im dual booting withxp and no more room) My question is 'Is it possible to copy and entire installation into another extra hard drive  without losing data?' If it can be done how will Grub handle the change?

---

### Post by maqtanim on 2011-03-03
No ... you cannot do it that way. 

You need to install Ubuntu in the other partition or other hard drive. After installing, you can copy paste /var/cache/apt/archives directory from the previous one, so that you donot need to install/download the applications/softwares again.

---

### Post by migrate from windows on 2011-03-03
Will that take care of all the updates that have been done so far? or I will need to update the new installation again from scratch?

---

### Post by Hedgehog1 on 2011-03-03
There are some other options to consider:

Moving your '/home' to the new disk, and leaving the 10 gig space for '/':  [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving") this means losing no data and not re-installing.

It is possible to copy and move partitions using gparted or clonezilla, but there are some steps to getting everything right.

***The Hedge***

:KS

---

### Post by migrate from windows on 2011-03-03
Thank you very much this seems to be a better option (moving the home partition) though I did not understand the steps involved ..I think I will get it with a little time spent on it .

---

### Post by Hedgehog1 on 2011-03-03
Because it separates your OS (in '/') from your data (in '/home'), if you hose your system, your data is safe.

It also makes for less stressful upgrades.

There are other tutorials on how to do this that are a little simpler.  This one is VERY complete, though.

---

### Post by mick222 on 2011-03-03
You could also try remastersys or create a data partition on the new drive and store files there,cd If you made the data partition fat32 you could also share it with xp

---

### Post by beew on 2011-03-03
Yeah I have a similar question and am interested in the answer to this question as well.
[URL="http://ubuntuforums.org/showthread.php?t=1689961&page=2"]http://ubuntuforums.org/showthread.php?t=1689961&page=2
[/URL]
Sydbat said that you can do it by simple cutting and pasting, I will try it out when I have a chance to think through it and do some research.

---

### Post by beew on 2011-03-03
> **mick222 said:**
> You could also try remastersys or create a data partition on the new drive and store files there,cd If you made the data partition fat32 you could also share it with xp

fat32 can only handle 4 G of data, no? Why not make the data partition ntfs? Linux can read ntfs without problem.

---

