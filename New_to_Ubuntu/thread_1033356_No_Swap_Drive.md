---
title: "No Swap Drive?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by fishman78 on 2009-01-07
Hi There,

   I was running htop last night and noticed that it indicated 0/0MB swap file.  I have an 8 GB partition for Swap, but it looks like ubuntu is not using it.  Is this normal?  I am running 8.10 64bit with 4GB of RAM.  Is the swap file not used sometimes?  Or do I need to manually assign the space?  I notice that Ubuntu is really slow to start up, but once it's running everything is really fast (maybe that's another question entirely?)  Thanks for the help!

fishman78

---

### Post by SunnyRabbiera on 2009-01-07
Linux doesnt use swap unless it is needed, swap is mainly there as a safty net even for large capacity memory like yours.
4GB of memory is more then enough to handle Ubuntu's workload and thensome.

---

### Post by evilkastel on 2009-01-07
I do not know about htop, but is normal for a system with so mcuh ram to barely or almost never use swap. Also OMG 8GB is A LOT of swap. In my opinion, way to much. You should never exceed 2 GB of swap. well, it's jus unnecessary.

---

### Post by hyper_ch on 2009-01-07
in htop it would show as 0/8128. So your swap is - for some reason - not activated.

Post your fstab file here.

---

### Post by fishman78 on 2009-01-07
It definetly indicated 0/0MB.  I'll post the output of fstab tonight when i get home from work.  Thanks.

I also thought that the swap file is normally 2x as large as your RAM.  Ubuntu formated the partition size for me so maybe I'm wrong about that....

---

### Post by Paddy Landau on 2009-01-07
I have 1Gb RAM and 2Gb swap. Very occasionally, when my computer is really, really busy with lots of programs, Ubuntu uses a little bit of the swap.

You really don't need 8Gb swap. 1Gb would more than suffice for 4Gb RAM, and I would be surprised if you ever used it.

---

### Post by mcduck on 2009-01-07
While you are at it, post the output of "blkid" as well. :)

The rule about swap being twice the RAM is a bit outdated, and doesn't really apply if you have 1GB or more of RAM (since with that much RAM there isn't usually any need for swapping).

If you have 1GB or more of RAM the amount of swap you need depends on if you wish to hibernate the machine or not. If you need the hibernating to work you need a bit more swap than you have RAM. If you don't need the hibernating feature and have more than 1GB of RAM then something like 512MB of swap should be enough.

---

### Post by fishman78 on 2009-01-07
Okay, I'll post that one too.  

I don't think I've ever put my comp to hibernate.  I usually just turn it off.  The drive is 500GB so I won't miss the wasted space.  As for apps I normally only run regular browser, email, and Vbox (WinXP VM).  The machine runs great once booted and I don't normally have any performance issues (except during bootup).

---

