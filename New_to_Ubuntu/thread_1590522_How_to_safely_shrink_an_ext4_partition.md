---
title: "How to safely shrink an ext4 partition ?"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by cap10Ibraim on 2010-10-08
I want it 100 % safe without any loss of data 
like windows 7 query for available space to shrink 
I'll use the live CD because I don't want it to be mounted
I just don't trust the resize command

---

### Post by alphacrucis2 on 2010-10-08
> **cap10Ibraim said:**
> I want it 100 % safe without any loss of data 
like windows 7 query for available space to shrink 
I'll use the live CD because I don't want it to be mounted
I just don't trust the resize command

Well back it up first. There is no other way. After all the power could go off during the resize operation and leave the partition borked.

---

### Post by mikechant on 2010-10-08
Using Gparted to do a simple ext4 shrink operation should be very reliable, and if you have a good power supply (e.g. in the UK the power is very reliable in most areas) you are very unlikely to get a power outage (probably more likely that you or your cat/dog/child will pull the power cord out accidentally!).

Also, if you are shrinking the partition from the end, no actual data is being moved/deleted/copied etc. so if there was a crash, it is highly likely the partition would still be usable and if not, that the testdisk tool would recover it.

However, there is never a 100% guarantee that *anything* computer related will work correctly. That's why, as alphacrucis2 says, you should back up if you want to be sure.

Anyhow, regardless of partitioning operations, your hard drive could fail at any time with total data loss. So if you value your data, you will be backing it up regularly already.

---

### Post by drs305 on 2010-10-08
If you have space (which may not be an option since you are trying shrink something ;-)  ) you could always use gparted to first copy the partition elsewhere and *then* shrink the original. 

I've never lost data using gparted but as has been said make sure you have backed up your data one way or the other before shrinking the partition.

---

### Post by cap10Ibraim on 2010-10-08
thanks everyone 
it was successful with gparted mainly because the partition was 30% full only

---

### Post by chandan_raka on 2013-03-05
> **cap10Ibraim said:**
> thanks everyone 
it was successful with gparted mainly because the partition was 30% full only


can you post the commands

---

### Post by overdrank on 2013-03-05
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

