---
title: "Vista partition/drive shrink problems..."
date: 2010-01-20
forum: New to Ubuntu
---

### Post by solutionorppt on 2010-01-20
Running Vista home premium 32-bit on an HP Slimline desktop w/ dual athlon 64's (2.6GHz, 2GB RAM)...

Anyone had any success shrinking the drive volume allocated to Vista using the built-in management tools?  I've read up on this and deduced that the main problem is that the master file table is written to the end of the volume and can't be moved by defragmenters, so despite the fact that I have over 100 GB of 'free' dive space, I can't create more than 14.5 GB of unallocated space to install Ubuntu for dual boot.

I've read that by temporarily turning off some system files like the pagefile system, you can free up more space but that the gain is not large compared to the amount of effort (or risk of error).  I've also read that by doing a wipe and fresh install with a drive shrink will move the MFT to 50% of the drive total volume each time. (i.e.- if you do this once, the new volume will be at 50% of total, 2nd time 25%, 3rd time 12.5%, etc.)

Does anyone experienced/knowledgeable on this one have any advice other than to purchase a more advanced defragmenter that will move the MFT? Thanks.

---

### Post by cloyd on 2010-01-20
I'm new at Ubuntu and Linux and not especially great at technical things, but I was able to shrink my Vista drive.  I had quite a bit of free space to start with.  I put Ubuntu on two computers to dual boot. One had a 260 gig hard drive, and I shrunk it down enough to give 36 gig for Ubuntu, and 4 gig for swap.  I could have shrunk it  more, and now I wish I had. I used the Vista utilities to shrink the drives.

On the other machine, I had a 500 git drive partitioned as C and D, with appox. 250 gig each.  I gave Ubuntu 100 gig that I took from the D drive. I wish I had given it more.   

Don't forget to defrag.  I am told, defrag twice . . . I assume to reduce the risk of losing data.  Back up before you shrink; everyone says there are inherent risks. I was lucky and didn't lose anything. Make sure you can reinstall Vista if you need to, and back up any data that you value.

But the question comes to mind, how big is your drive?    

I don't know if anything I said here is helpful, but I am interested in how it works out for you. Good luck.

---

### Post by solutionorppt on 2010-01-20
The drive in question is a 320 GB with a 9 GB recovery partition. I have 171 GB of free space of the 311 GB remaining after the recovery partition. I have defragged multiple times both before and after shrinking the windows partition to get unallocated space.

---

### Post by cloyd on 2010-01-21
Ok. I've been off the net a while. 

In fact, you may need someone with more experience than I, but do I get this straight that when you go to the Vista utilities, and click on shrink drive, it tells you the max shrink available is 14.5 gig?  Or is some other utility or the live cd installer telling you all you have available is 14.5 gig? 

 I had no problem, but I first shrunk with Vista to gain the unallocated space, and then actuallly created the Ubuntu partition with the live cd using option "use larges unallocated space."  

You may understand all of this, but I had some written instructions, and it took me a long time to get it through my head that I created the empty space with Vista, and then created the partitiion in the empty space with the live cd.  Forgive me if I am not recognising your problem entirely.

Others are encouraged to chime in.

---

### Post by lisati on 2010-01-21
> **solutionorppt said:**
> The drive in question is a 320 GB with a 9 GB recovery partition. I have 171 GB of free space of the 311 GB remaining after the recovery partition. I have defragged multiple times both before and after shrinking the windows partition to get unallocated space.

You might also want to check the temporary files on your system. The "standard" Windows way is from Start->(All) Programs->Accessories->System Tools->Disk Cleanup. This, however, doesn't always get read of *all* temporary files. One way is to click on Start->Run and typing in the following in the popup box:```
%temp%
``` You can then review and delete a bunch of temporary files - you might be surprised what "rubbish" is there! (See link in my sig for another way, tested with Win98SE, XP and Vista Home Premium)

---

### Post by presence1960 on 2010-01-21
Turn off System restore until after the resize. Make sure you have a backup before you do so. That will help the resize also.

---

### Post by lumpyfred on 2010-01-21
I was having this same problem when I was setting up a Windows 7/Ubuntu Karmic dual boot for the first time last night. I found this howtogeek guide to be extremely helpful:  

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

What I ended up having to do after following all of the steps in this guide was to download Perfect Disk 10 @ [http://www.perfectdisk.com/](http://www.perfectdisk.com/) (I just downloaded the FREE 30 day trial and will uninstall when that is over) and used the Free Space Consolidation Feature, which completely defragged my drive and allowed me to free up almost 150 gigs of space. Before I did this Windows would not let me shrink the partition by anything at all. 

Again, I did this all just last night and went from being able to shrink zero space to almost 150 gigs just by following these steps. Hope this helps.

---

### Post by solutionorppt on 2010-01-22
Thanks Lumpyfred, that worked like a charm!

---

