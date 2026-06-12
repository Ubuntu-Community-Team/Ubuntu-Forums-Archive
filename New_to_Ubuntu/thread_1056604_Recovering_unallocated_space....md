---
title: "Recovering unallocated space..."
date: 2009-01-31
forum: New to Ubuntu
---

### Post by akelsall on 2009-01-31
I've seen several posts concerning this problem, but no good solution as of yet. Here's the deal.

I have two large areas of my disk showing up as unallocated in GParted. I already have 4 partitions created (root, home, swap, and extended), so I can't create a new partition.

How the heck do I recover these unallocated regions of my disk? I'm unable to use 250 gig of space because of this problem. There has to be a way to recover this space. Can someone please give me (and everyone else with this problem) a hand?

Thanks,

Andy

---

### Post by taurus on 2009-01-31
Can you take a screenshot of gparted, displaying your harddrive layout?

---

### Post by unutbu on 2009-01-31
Tomorrow (1330 UTC), veterans of ubuntuforums will be on IRC #ubuntu-classroom on freenode.net specifically to talk about and field questions on the issue of partitioning: [http://ubuntuforums.org/showthread.php?t=1048980](http://ubuntuforums.org/showthread.php?t=1048980). 

I'm confident you can get an answer here tonight, but just in case you or others might be interested, I thought I'd mention it...

---

### Post by grainbarcelona on 2009-02-01
Same problem here. Unallocated space which I would like to add to my SDA4 home partition? How do I do this?

Screenshot of Gparted attached

Thanks for any help

---

### Post by taurus on 2009-02-01
The problem is that you run gparted from Ubuntu which means you cannot resize your Ubuntu while you are using it.  Therefore, you have to do it from the LiveCD or with GParted LiveCD,   [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

And since the unallocated is at the beginning of the harddrive, you have to add that to /dev/sda1, then shrink /dev/sda1 and add that space to /dev/sda2.  Then, shrink /dev/sda2 and add that space to /dev/sda3.  Then finally, shrink /dev/sda3 and add that space to /dev/sda4.

Or maybe there is a way to by pass the first three partitions and "stick" the unallocated space to /dev/sda4 directly!

---

### Post by grainbarcelona on 2009-02-01
"Or maybe there is a way to by pass the first three partitions and "stick" the unallocated space to /dev/sda4 directly!"

That's what I would like to know, how to do that!

thnx!

---

### Post by taurus on 2009-02-01
> **grainbarcelona said:**
> "Or maybe there is a way to by pass the first three partitions and "stick" the unallocated space to /dev/sda4 directly!"

That's what I would like to know, how to do that!

thnx!

I don't even think that is possible.  Maybe somebody has done it can jump in and show you how.

---

### Post by grainbarcelona on 2009-02-01
Anyone has a clever idea on this? Or do I have to follow Taurus suggestion to do the move&shrink process 3 times? Which I can do but it's a bit tedious.
Thnx!

---

### Post by louieb on 2009-02-01
Looks like sda1 is empty or nearly so. I'd probably just copy the data off sda1,delete it, and create it again using all the unallocated space and copy the data back. Then you can mount it on something like /media/stuff.

---

### Post by caljohnsmith on 2009-02-01
**Akelsall**, in order for us to get an idea of the physical layout of your partitions, how about first posting:
```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by akelsall on 2009-02-01
Well, I got a bit impatient and tried finding a fix myself. About 200 Gig of unallocated space was "outside" both my primary partition and my extended partition (not sure how that happened). So, I grew my extended partition to it's max size and was able to bring that 200 gig of unallocated space inside the extended partition. 

**********************************************************************
As someone mentioned in one of the posts, all this must be done while running from the LiveCD, which is what I did initially)
***********************************************************************

At that point, I created three 50 gig partitions from that chunk, but when I went to partition the remaining 50gig, it wouldn't allow me (see screen captures for more info). 


When I initially rebooted the first time, I got dumped into some type of "maintenance shell" and I found the reason for that (on another post) was because re-sizing the partitions sometimes (or maybe always) effects some of the UUIDs found in fstab. That was my case. I compared the output of the command  sudo /sbin/vol_id -u /dev/sdaX with the UUID found in fstab (for each of the partitions on my harddrive). I found just one partition that didn't match up with the UUID listed in /etc/fstab. So, once I fixed that, I rebooted again.

This time, I got to the login prompt, but it told me it couldn't find my home directory. SOOOOO, I rebooted again, this time successfully getting to my desktop (using my standard login credentials).

I still have the same issue with the error messages though. I can partition /sda16 for some reason. I gives me the error message shown in the screen shot. Any idea what's going on now, and what else I may have hosed?

Oh, and I just now see that there's a different "view" of my hard drive between Nautilus and the "computer file browser". For some reason, Nautilus doens't show the three partitions I created (and named "FREE1", "FREE2", and "FREE3"). arrggggghhhhh

Thanks,

Andy

---

### Post by unutbu on 2009-02-01
SATA drives have a limit of 15 partitions. This means that sda15 is the last partition you'll be able to successful make. Delete sda16 -- it simply will not work. See [http://tldp.org/HOWTO/html_single/Partition/#logical](http://tldp.org/HOWTO/html_single/Partition/#logical)

The GParted screenshot shows that "FREE1", "FREE2", and "FREE3" (sda13, sda14, sda15) are not mounted. This is why they are not showing up in Nautilus.

If you type
```

invoke-rc.d hal restart
```
You might be able to coax HAL to automount them for you. Otherwise, a reboot should work.

---

### Post by akelsall on 2009-02-02
unutbu, thanks for the tip on partition limitations for SATA drives. For some reason, I thought I had read you could have 32 or 64 partitions, but maybe that's with using LVM. I ended up "redistributing" the space on sda16 between sda13 and 14 and that effectively deleted sda16. Thanks a lot for you help. 

Also, you're correct about the partitions marked FREEx. I wasn't even thinking about them not being mounted. Thanks for pointing out my oversight.

Andy

---

