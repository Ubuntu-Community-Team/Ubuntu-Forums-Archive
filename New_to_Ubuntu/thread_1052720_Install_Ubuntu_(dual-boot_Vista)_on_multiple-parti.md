---
title: "Install Ubuntu (dual-boot Vista) on multiple-partitioned drive"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by jezebel on 2009-01-28
Hi all.

Well, I've got my newly built machine up and running smoothly with Vista.

Now I want to re-install Ubuntu and have a dual-boot system again. However, I'm not sure I remember how to install with all the complicated partitions that I've got.

I have 1TB drive, partitioned like this: 100 gb = Vista OS; 250 gb=photos; 250gb=Other (docs, vids, etc.), and the rest just sitting there waiting to be used.

My concern is, when I want to install Ubuntu, how will I know where to install it where it won't wipe out any of my other data??

Sorry for such a basic question...

---

### Post by dcn427 on 2009-01-28
i new to ubuntu, but i have noticed that when i installed with windows runnit, it set it up to dual boot. try runing it as inside windows and it should be good.

---

### Post by jezebel on 2009-01-28
Thanks - I'm not too worried about dual booting once it's installed, as I had it running great with XP, Vista and Ubuntu triple booting at one point. But since I've rebuilt my machine, changed around my drives, etc... I need to re-install.

My concern is how do I know where to install Ubuntu, how to set up space for it, where I won't accidentally install it over my other (precious) data.

---

### Post by jezebel on 2009-01-28
AHA!

dcn427 - I didn't know about Wubi, and running Ubuntu in Windows!

I just downloaded and read Keir Thomas' Beginner's Guide, and see what you meant.

I'll give that a try.

Tracy

---

### Post by Praxicoide on 2009-01-28
There's little chance of confusion, because if you use the live CD, it will show your current partitions in a nice graph. Your Windows partitions will be labeled as using the ntsf filesystem. So there will be three partitions, and a large unallocated space. You won't touch any of the partitions, except to set up the mount points. 

I recommend you to use the manual option and create an extended partition on the empty space of your drive. You can then set up logical partitions inside the drive to assign to Ubuntu.

As long as you don't choose the "delete partition" option or decide to format any of the existing partitions, you should be fine.

---

