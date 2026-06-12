---
title: "Natty swapfile fails to clear after hibernate wakeup"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-07-04
Hi,   Am I right in expecting my swapfile to clear after waking up from hibernation?

I'm seeing a cumulative build-up of swapfile each time I wake up from hibernation until after about 3 or 4 hibernates there's no more free swapfile and I can't hibernate any more.    

Here are some typical figures taken from my System Monitor Resources tab:
```

     After      After 1st     After 2nd       After 3rd      After 4th
     Restart    hibernate     hibernate	      hibernate      hibernate 

    Mem = 26%      20%   	23.8%	        20.5%		 21.3%
    Swap = 0     19.5MiB         80MiB 	        175.3MiB        209.3MiB 
   (Swap %)      (2.8%)        (11.3%)          (24.8%)         (29.7%) 
```

Unless my memory gets fully used up,  shouldn't my swapfile clear back to 0 after each wakeup so that it has plenty of capacity to receive new hibernation data next time?     

Could this be a bug, or is there some way I can control clearing of swapfile?

By the way,  this post is an update and bump on [http://ubuntuforums.org/showthread.php?p=10976614](http://ubuntuforums.org/showthread.php?p=10976614) which seemed to die last week.  Grateful any suggestions?

---

### Post by amjjawad on 2011-07-04
You bump a thread by starting a new one? it's a bad idea!

---

### Post by Enigmapond on 2011-07-04
It holds it...just in case. Run:

```
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
```

This will clear the memory cache to all but what's currently being used.

Cheers!

---

### Post by Sleepy-zz-John on 2011-07-04
> **amjjawad said:**
> You bump a thread by starting a new one? it's a bad idea!
Oh sorry!  :redface:   The other thread had run out of steam without a good answer,  so I thought people must have got tired and bored with its detail.  A fresh start seemed to make sense.

---

### Post by Sleepy-zz-John on 2011-07-04
Thanks Enigmapond.    However I've just tried that command and it doesn't seem to be having any effect.    I watched  in System Monitor Resources tab as I entered it and the swap line didn't alter at all.    I then tried to hibernate and that failed and went into suspension instead due to not enough swapfile.   When I returned from suspension,  I could see the swap line figure has increased.   Apart from sudo asking me for my password, the command didn't produce any response in terminal.

---

### Post by dFlyer on 2011-07-04
Just copy and paste this to a command line:

sudo sync
sudo su
echo 3 > /proc/sys/vm/drop_caches

the above will clear your cache

sudo swapoff /dev/your swap drive
sudo swapon /dev/your swap drive

change your swap drive to the device used for swap on my system it's sda5

This will clear your swap. If you don't know what drive your swap is on check your fstab file in the /ect directory

You might want to think about increasing the size of your swap file as it is really small.

---

### Post by Sleepy-zz-John on 2011-07-04
> **dFlyer said:**
> Just copy and paste this to a command line:

sudo sync
sudo su
echo 3 > /proc/sys/vm/drop_caches

the above will clear your cache 
Thanks for the suggestion,  but it doesn't seem to work.  The first two lines give me a root prompt,  the third line enters OK but my swapfile indication in System Monitor Resources remains unchanged
> 
sudo swapoff /dev/your swap drive
sudo swapon /dev/your swap drive

change your swap drive to the device used for swap on my system it's sda5

This will clear your swap. If you don't know what drive your swap is on check your fstab file in the /ect directory

I presume I was supposed to exit from my root prompt before entering these next commands.  
After I exited,  /etc/fstab showed my swap to be on sda4.   
sudo swapoff /dev/sda4 briefly sent my swap indication up to 100% and then down to zero.
I then entered sudo swapon /dev/sda4  and after that I tried to hibernate,  but it failed and went into suspend instead. 
>  You might want to think about increasing the size of your swap file as it is really small.
But the odd thing is that after a restart,  I have no problem hibernating with 4 or 5 windows open.   After one hibernation I can still hibernate the same 4 or 5 open windows again.     But after 2 or 3 hibernations,  I still can't hibernate any more, not even if I reduce down to 3 open windows,   until I've done a restart.
Despite that swapoff command,  something is still building up in my swap file and preventing me from hibernating again.
OK, I need to get some sleep now as it's 01:45am here,  but hope to resume with some more tests later in the day.
  Thanks again

---

### Post by Sleepy-zz-John on 2011-07-31
I'm still having the same problem with Natty,  namely that after waking up from one or two previous hibernations,  a subsequent hibernation attempt invariably fails with a not enough swapfile prompt.      

I have followed the above suggestions and cleared my cache with ```
echo 3 > /proc/sys/vm/drop_caches   
``` followed by ```
sudo swapoff /dev/sda4
sudo swapon /dev/sda4
```  and I've monitored my swap history record as displayed in System Settings - System Monitor - Resources - Memory & Swap History drop typically from around 45% to 0%.    However even with my swap displaying 0%,   if I'm trying a 2nd or 3rd hibernation attempt since my last restart,  it fails with that not enough swapfile prompt.

On the other hand,  1st hibernation attempts after a restart never fail,  even if do them with several windows open.   

I'm now somewhat perplexed as to what's actually causing this.   If my 0% swap display in Memory & Swap History is to be believed,  it's not simply a failure to clear the swapfile.    Something else must be ***"remembering"*** previous hibernation data.   

This does seem to be a Natty-related issue because I was previously happily doing multiple hibernations with Karmic on the same size partitions on the same HD without this problem.

By the way, when hibernation fails like this,  suspend still works OK as a last resort.

So now, I'm looking for bright ideas and/or suggestions of further tests to try and diagnose what's really going on here.

---

### Post by coffee412 on 2011-08-01
> **Sleepy-zz-John said:**
> I'm still having the same problem with Natty,  namely that after waking up from one or two previous hibernations,  a subsequent hibernation attempt invariably fails with a not enough swapfile prompt.      

I have followed the above suggestions and cleared my cache with ```
echo 3 > /proc/sys/vm/drop_caches   
``` followed by ```
sudo swapoff /dev/sda4
sudo swapon /dev/sda4
```  and I've monitored my swap history record as displayed in System Settings - System Monitor - Resources - Memory & Swap History drop typically from around 45% to 0%.    However even with my swap displaying 0%,   if I'm trying a 2nd or 3rd hibernation attempt since my last restart,  it fails with that not enough swapfile prompt.

On the other hand,  1st hibernation attempts after a restart never fail,  even if do them with several windows open.   

I'm now somewhat perplexed as to what's actually causing this.   If my 0% swap display in Memory & Swap History is to be believed,  it's not simply a failure to clear the swapfile.    Something else must be ***"remembering"*** previous hibernation data.   

This does seem to be a Natty-related issue because I was previously happily doing multiple hibernations with Karmic on the same size partitions on the same HD without this problem.

By the way, when hibernation fails like this,  suspend still works OK as a last resort.

So now, I'm looking for bright ideas and/or suggestions of further tests to try and diagnose what's really going on here.

Caught your post this morning and thought I would try and help you out. 

When Hibernating, Linux will save ALOT of info about the active state of your system before hibernation. Evidently your swap space is too small to hold this info at the time of hibernation (sometimes). 

Therefore, What you should do is shrink one of your partitions and take the recovered space and grow your swap partition with it. 

If you post the output of "fdisk -l" and "mount" we can see what things are looking like and I might be able to advise further.

coffee

---

### Post by Sleepy-zz-John on 2011-08-01
> **coffee412 said:**
> Caught your post this morning and thought I would try and help you out.
Many thanks. Much appreciated, specially as this thread has already run for a while  :) 
> *When Hibernating, Linux will save ALOT of info about the active state of your system before hibernation. Evidently your swap space is too small to hold this info at the time of hibernation (sometimes). *
Yes,  others have already hinted at my swap partition being too small and I'm beginning to agree,  but still trying to understand how Natty is so much more resource-hungry than Karmic, and why it's only my 2nd or 3rd hibernates after a restart that fail and my first is always successful.  In other words what info is being carried forward and accumulating from previous hibernations,  and why doesn't that info get deleted by my drop_caches and swapoff commands?  Where is that info lurking when my Swap History shows I've reduced swap content to zero?     
> *Therefore, What you should do is shrink one of your partitions and take the recovered space and grow your swap partition with it.*
I understand what you're suggesting here but worried that because this info appears to accumulate and increase after each hibernate, then whatever extra swapfile we decide to allocate will only get swallowed up again during subsequent hibernates and sooner or later I'll be back with the same old problem!  
>  *If you post the output of "fdisk -l"......*[QUOTE]
Dunno why but neither "fdisk -l"  nor "fdisc -l sda" produce any output at all.  However here's the content of my /proc/partitions
```

 major  minor  #blocks  name

   8        0   58605120 sda
   8        1   28587636 sda1
   8        2   21101377 sda2
   8        3          1 sda3
   8        4     722925 sda4
   8        5    8193118 sda5
   8       16    7843840 sdb
   8       17    7839808 sdb1
```
sda1 is my 29GB extn4 Natty partition (19% used)
sda2 is my 22GB ntfs Win XP partition (55% used)
sda3 is my 8.4GB Extended Data partition
sda4 is my 740MB Swap space
sda5 is my 8.4GB Data partition (34% used)
[QUOTE]*.... and "mount" *
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sda5 on /media/DATA type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1 on /media/KINGSTON_ type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```
>  *we can see what things are looking like and I might be able to advise further.*
Yes, thanks, and I'd certainly appreciate your advice.   Clearly I could easily spare some space from my sda1 and allocate it to sda4,  but with the way additional info seems to be accumulating after each hibernate,  isn't this going to just result in me being able to do a maximum of (for example) 4 hibernates before I need a restart, instead of my present 1 or 2 hibernates? 
The number of hibernates Natty lets me do before telling me there's no free swapfile actually depends of course on how much stuff (how many windows & how many tabs etc.) I have open when I hibernate.   
If I don't do any swapoff command after a hibernate,  I can clearly see my swap content accumulating each time.   See that tabulated in my 1st post on this thread.

---

### Post by psusi on 2011-08-01
> **Sleepy-zz-John said:**
> Hi, Am I right in expecting my swapfile to clear after waking up from hibernation?

No.  Whatever was in swap when you hibernated will still be there when you resume.  Before you hibernate, the first thing the system does is free up at least 50% of memory, which may involve pushing some more stuff out to swap.

> **Sleepy-zz-John said:**
> I'm seeing a cumulative build-up of swapfile each time I wake up from hibernation until after about 3 or 4 hibernates there's no more free swapfile and I can't hibernate any more.

Sounds like you have some program with a memory leak hogging more and more ram until too much is in use to hibernate.  Look at your memory usage and try to find the offending program.  Hibernating and waking up by itself should not cause this.

> **dFlyer said:**
> Just copy and paste this to a command line:

sudo sync
sudo su
echo 3 > /proc/sys/vm/drop_caches

the above will clear your cache


That's not helpful.  All it does is slow down your machine for a while since the disk will have to be read when it could have been satisfied from the cache.

---

### Post by Sleepy-zz-John on 2011-08-01
> **psusi said:**
> *No.  Whatever was in swap when you hibernated will still be there when you resume.  Before you hibernate, the first thing the system does is free up at least 50% of memory, which may involve pushing some more stuff out to swap.*
Thanks psusi,  but since I've been trying a swapoff command after waking up,  and I can see that reduces my swap to zero, but subsequent hibernate attempts are still failing,   where could that "stuff" be going ? :confused:  
It doesn't appear to be going back into memory.   Look at my table of memory and swap in my OP #1 
> *Sounds like you have some program with a memory leak hogging more and more ram until too much is in use to hibernate.  Look at your memory usage and try to find the offending program.*
Sounds like a reasonable theory,  but in that case why wouldn't I be seeing cumulative increases in total memory usage after each hibernate? 
This trouble started with my upgrade from Karmic to Natty,  so that puts Natty itself as a prime suspect for causing this memory leak.  I didn't introduce major new programmes at the time I upgraded.  Admittedly Natty came with a new version of Firefox, and soon after the upgrade a new version of SeaMonkey came along,  but nothing else major and new to suspect.
I'll have another look at my memory usage,  though,  and see if I can find out how to get a breakdown of that.   
>    * Hibernating and waking up by itself should not cause this.*
Noted,  thanks.
> 
*That's not helpful.  All it does is slow down your machine for a while since the disk will have to be read when it could have been satisfied from the cache.*
Noted, thanks.

---

### Post by coffee412 on 2011-08-01
Just for comparison, My fedora box has a swap partition size of 3.9 gig and was setup when using only 2gig or ram. I would really entertain the idea of increasing the swap space and see how it goes.

Good luck,
coffee

---

### Post by psusi on 2011-08-02
> **Sleepy-zz-John said:**
> Thanks psusi,  but since I've been trying a swapoff command after waking up,  and I can see that reduces my swap to zero, but subsequent hibernate attempts are still failing,   where could that "stuff" be going ? :confused:  
It doesn't appear to be going back into memory.   Look at my table of memory and swap in my OP #1 

Your OP did not mention anything about swapoff, just hibernate and resume.  Take a look at free -m before and after the swapoff, and you should see the swap moved back into ram.  Also what exactly does free -m show when you can no longer hibernate?

---

### Post by Sleepy-zz-John on 2011-08-03
> **psusi said:**
> Your OP did not mention anything about swapoff, just hibernate and resume.  Ah, sorry for the misunderstanding,  the suggestion to try swapoff didn't come until post #6  
> *Take a look at free -m before and after the swapoff, and you should see the swap moved back into ram.  Also what exactly does free -m show when you can no longer hibernate?*
Here's a sequential log of several free -m reports I've done at different stages of multiple hibernates and swapoffs:
```

AFTER A RESTART:
             total       used       free     shared    buffers     cached
Mem:          1244        844        400          0         65        482
-/+ buffers/cache:        296        948
Swap:          705          0        705

AFTER ONE WAKEUP:
             total       used       free     shared    buffers     cached
Mem:          1244        582        662          0         18        302
-/+ buffers/cache:        261        983
Swap:          705        132        573

AFTER SWAPOFF-SWAPON:
             total       used       free     shared    buffers     cached
Mem:          1244        733        511          0         28        378
-/+ buffers/cache:        325        919
Swap:          705          0        705

AFTER 2nd WAKEUP:
             total       used       free     shared    buffers     cached
Mem:          1244        575        669          0         23        260
-/+ buffers/cache:        291        952
Swap:          705        132        573
	
AFTER SWAPOFF-SWAPON:
             total       used       free     shared    buffers     cached
Mem:          1244        678        566          0         27        322
-/+ buffers/cache:        328        916
Swap:          705          0        705

System crashed (due to an unrelated webcam issue) so had to begin again with a new restart at this point

AFTER 2nd WAKEUP and UNABLE TO HIBERNATE THIS TIME:
             total       used       free     shared    buffers     cached
Mem:          1244        636        608          0         26        323
-/+ buffers/cache:        286        958
Swap:          705        132        573

AFTER SWAPOFF-SWAPON and STILL UNABLE TO HIBERNATE:
Mem:          1244        695        549          0         26        333
-/+ buffers/cache:        335        909
Swap:          705          0        705
```

I'm not sure what to make of all this.  There are some cases where my used mem + buffers/cache was > total swap and I could still hibernate, yet other cases where my used mem + buffers/cache was > total swap and I was unable to hibernate.

Looks like there should be a clue here,   but I still don't get it.  

Referring back to my post #10 here,  I'm thinking I ought to try increasing my swap partition sda4 by about 800MB which I would obtain by reducing my Natty partition sda1 by 800MB.   sda1 is only 19% used.   I got as far as booting from my Natty Live CD and looking at the partitioning tool there,  but I've come unstuck on how to safely remove 800MB from the 29.3GB of sda1 without wrecking any of my current system files that are occupying 5.8GB on it.  The partitioning tool talks of reformatting,  which I'm fearing would erase my whole system.  

If you agree that reallocating 800MB from my sda1 to sda4 is a good approach,  I'd appreciate a little guidance on the partitioning.

Many thanks for your continuing help, psusi.

---

### Post by psusi on 2011-08-03
Yes, you just don't have enough swap.  In that example you only have 573 mb of free swap, but over 600mb of ram to put in it.  You can resize your partitions on the livecd using gparted.  Just drag the sliders around to move the partition boundaries around so that swap is a little bigger.

As an alternative, you can adjust your settings to get the kernel to try and squeeze more out of ram ( dropping cache ) to make room to hibernate:

```

sudo -s
cat /sys/power/image_size
echo 0 > /sys/power/image_size

```

Also you might want to install the uswsusp package.  It enhances the hibernation process a bit, including enabling compression of the data being written out so the process will go faster.

---

### Post by Sleepy-zz-John on 2011-08-06
> **psusi said:**
> ..... You can resize your partitions on the livecd using gparted.  Just drag the sliders around to move the partition boundaries around so that swap is a little bigger.

Yes, thanks, that's what I want to do,  but I'm still stuck on how to safely remove 800MB from my sda1's 29.3GB without risking losing any of my current system files that are occupying 5.8GB on it.  My worry is because gparted talks of "reformatting", which I'm fearing will erase my whole partition.     How can I ensure that none of that 5.8G of Natty files disappears when I remove 800MB from sda1?   Maybe I'm misunderstanding something,  but I thought "reformat" meant erasing everything on the partition.  Please can you put me straight on that?  
 
> [i]
As an alternative, you can adjust your settings to get the kernel to try and squeeze more out of ram ( dropping cache ) to make room to hibernate:

```

sudo -s
cat /sys/power/image_size
echo 0 > /sys/power/image_size

```

Also you might want to install the uswsusp package.  It enhances the hibernation process a bit, including enabling compression of the data being written out so the process will go faster.[/i]

Yes, I want to look at these alternatives once I've increased my swap.  I want to check first whether each successive hibernate is still cumulatively adding to the swap content, and see if I still eventually run out of swap after several hibernates.

Like you psusi, I saw in that example how there was a case of more content in ram than there was free swap,  and that's why it failed,  but as far as I can see I'm getting other examples where theoretically it ought to fail and doesn't,  and others where it oughtn't to fail and does.  What I'm saying is that I still don't completely "get" the whole picture of how it's working.     Anyway, perhaps once I've got a larger swap partition that picture will emerge more clearly.   

Anyway,  once again, thanks for the support. :)

---

### Post by psusi on 2011-08-06
Choose "resize", not "reformat".

---

### Post by Sleepy-zz-John on 2011-08-07
I've been back into my Natty Live CD Install option intending only to double check the procedure and warning messages, not to actually go through with any changes until I'd discovered how to back up the complete 5868 MB contents of my Natty partition.  I didn't find a "resize" option there as such but proceeded cautiously, selecting /dev/sda1 extn 4 and pressing "Change".

I was able to edit my partition size there down from 28500 to 27700,  select "Extn 4" and Mount /    There was a Format option box there which I very deliberately left blank.

This brought up a note that said  "Before you can select a new partition size, any previous changes have to be written to disc.  You cannot undo."

I pressed "Continue" which then brought up this further note:   "The file system on sda1 assigned to / has not been marked for formatting.  Directories containing system files (/etc, /lib, /usr, /var...) that already exist under any defined mountpoint will be deleted during the install.  Please ensure that you have backed up any critical data before installing"   

At this point I chickened out and pressed QUIT because I hadn't backed up.   

However before leaving Natty Live CD completely,  I had a look in Installed Applications - gparted  and noticed there that /dev/sda1 extn 4 was showing a reduced size of 25.8GiB (instead of 28.5),  used files of 5.45GiB (instead of 5868MB). and an unallocated space of 1.47GiB.  This was a bit worrying because I didn't think I'd saved anything to disc.  But perhaps these were just preparatory figures saved in ram.   I decided I'd better completely quit the Live CD at this point.

When I tried to boot my computer from its own hard disc,  Grub came up and gave me the usual booting options,  and I let it try the usual first choice Ubuntu 11.04.    But that now fails to boot and only gives me a BusyBox initramfs prompt.  Recovery mode also fails exactly the same with dmesg showing: 

mounting /dev on /root/dev failed
mounting /sys on /root/sys failed
mounting /proc on /root/proc failed

Oh dear!    So back to my Natty Live CD again where under the home directory I can see my 28GB file system sda1 reporting:

 Error mounting:  wrong fs type, bad option, bad superblock on /dev/sda1
 Missing codepage or helper program or other error

Back again on initramfs I then tried mount/dev/sda1 which reported:
  "can't read '/etc/fstab'  no such file or directory

And dmesg reported: 
  EXT 4 -fs (sda1): bad geometry: block count 6958007 exceeds size of device 6762695

So finally back again to Natty Live CD Installation and try to see if I could get it to repair the damage.   But no,  this time I'm getting 
"ubi-partman crashed    failed exit code 14"

I'm afraid my amateur dabbling only seems to be digging me deeper into the mire,  so all I can say now is HELP!  WHAT SHOULD I DO NEXT?

I'll try and attach some logfiles to a subsequent post in case these help.

---

### Post by Sleepy-zz-John on 2011-08-07
Here in a .tar.gz are four logfile attachments relating to my previous post #19.  You may find them somewhat repetitive.

---

### Post by psusi on 2011-08-07
You are running the Ubuntu installer, not gparted.

---

### Post by Sleepy-zz-John on 2011-08-07
> **psusi said:**
> You are running the Ubuntu installer, not gparted.
OK, noted.   Sorry,  I misunderstood that the installer uses a built-in version of gparted. However I did subsequently run the gparted in Installed Applications (para 6 of my post #19) and it would be that which generated my attached gparted log.

Hoping now that I might be able to get some emergency step-by-step guidance to see if there's any way of restoring the contents of my sda1 and recover from the mess I've got into  :sad:   I'm not so clever with all this, and  of course all I've got to work with in this emergency situation is my live Natty CD :confused:

---

### Post by psusi on 2011-08-07
It sounds like you had the installer reformat the drive.  You might try using testdisk as a last ditch effort, but you are now firmly in restore from backup territory.

---

### Post by Sleepy-zz-John on 2011-08-07
> **psusi said:**
> It sounds like you had the installer reformat the drive.
Hmmm... thanks,  but I don't understand how I could have done that (paras 1 and 5 in my #19 post).   

Admittedly I'm groping in the dark here,  but doesn't the fact that 5.45GiB is still showing as used (para 6 of my #19 saga) and the blockcount figures in para 12 indicate that sda1 still has most of my content there? 
> *  You might try using testdisk as a last ditch effort,*
Unfortunately testdisk isn't installed as a terminal command on the Natty Live CD I'm now reduced to operating on. 

Although ubi-partman in install still crashes every time I try to go back in there,  I find I can still open GParted which is sporting a Resize/Move button.   I'm wondering if I would be compromising my chances of recovering my sda1 contents if I were to try and resize the currently indicated 25.8GiB there to the 27700 I was originally aiming the new size of sda1 to be?    There's an unallocated 1.47GiB on my sda that's showing there now which I didn't have before.   If so this dummy would certainly appreciate some step-by-step guidance against getting into even deeper trouble. 
> * but you are now firmly in restore from backup territory.*
Well that would be turning this into such an unmitigated disaster that I want to be 100% sure I've exhausted every avenue before I really do press a format button.   No-one appears to have looked at the logfiles I sent,  and I'm still hoping that if expert eyes were to scan those,  they might just be able to spot something I've missed.

---

### Post by psusi on 2011-08-08
> **Sleepy-zz-John said:**
> Hmmm... thanks,  but I don't understand how I could have done that (paras 1 and 5 in my #19 post).   

It sounds like you went into the installer, deleted your existing partition, and created a new one with a slightly different size, which is now empty.

> **Sleepy-zz-John said:**
> Unfortunately testdisk isn't installed as a terminal command on the Natty Live CD I'm now reduced to operating on. 

So.... install it?

> **Sleepy-zz-John said:**
> I'm wondering if I would be compromising my chances of recovering my sda1 contents if I were to try and resize the currently indicated 25.8GiB there to the 27700 I was originally aiming the new size of sda1 to be?    

Resizing now will definitely get you into more trouble.

---

### Post by Sleepy-zz-John on 2011-08-08
> **psusi said:**
> It sounds like you went into the installer, deleted your existing partition, and created a new one with a slightly different size, which is now empty.
No,  that's absolutely not what happened.  If that were the case,  how come 5.45GiB is still showing as used (para 6 of my #19 saga) and the blockcount figures in para 12?    I don't understand exactly what's happened or how it could have occurred, but there are clear indications that my sda1 partition isn't empty even if its contents aren't accessible.       
> *So.... install it?* No, can't install anything when you're operating in Live mode off a CD like I am. There's no space to save any new progs to.  No HD, and all the RAM is occupied with the operating system basics.
> *Resizing now will definitely get you into more trouble.*
How do you figure that?   What sort of trouble are you envisaging?   Anyway, even in the worst case of having to completely re-install Natty in my sda1 partition space that's currently broken,   some kind of resizing would be needed first in order to repair the bad geometry it's currently exhibiting.  Something needs to be done to stop ubi-partman crashing every time I try to go in there,  but the trouble is I don't know what,  and that's where I'm seeking further guidance.

---

### Post by psusi on 2011-08-08
> **Sleepy-zz-John said:**
> No,  that's absolutely not what happened.  If that were the case,  how come 5.45GiB is still showing as used (para 6 of my #19 saga) and the blockcount figures in para 12?    I don't understand exactly what's happened or how it could have occurred, but there are clear indications that my sda1 partition isn't empty even if its contents aren't accessible.

Depending on where you look, you will see used space on a freshly formatted partition for the overhead of the filesystem itself.  If you don't see any files, then they aren't there.  You might try fscking the partition just to make sure the count is accurate though.

> **Sleepy-zz-John said:**
> No, can't install anything when you're operating in Live mode off a CD like I am. There's no space to save any new progs to.  No HD, and all the RAM is occupied with the operating system basics.

Yes, you can.  If you have less than 1 gb of ram then you won't be able to install much, but you can certainly install a single small package like testdisk.

> **Sleepy-zz-John said:**
> How do you figure that?   What sort of trouble are you envisaging?   Anyway, even in the worst case of having to completely re-install Natty in my sda1 partition space that's currently broken,   some kind of resizing would be needed first in order to repair the bad geometry it's currently exhibiting.  Something needs to be done to stop ubi-partman crashing every time I try to go in there,  but the trouble is I don't know what,  and that's where I'm seeking further guidance.

Because resizing is going to move things around and likely overwrite more of any data that may still be there.  The bad geometry is because you changed the partition table and the fs contained in the now smaller partition still thinks it is the full size.  You need to repair the partition table and recover the fs, without doing the usual moving of files around that a resize normally entails.  That is where testdisk comes in.

---

### Post by Sleepy-zz-John on 2011-08-10
> **psusi said:**
> Depending on where you look, you will see used space on a freshly formatted partition for the overhead of the filesystem itself.  If you don't see any files, then they aren't there.  You might try fscking the partition just to make sure the count is accurate though.

Thanks.  Things are beginning to make a little bit more sense to me now:)

No but as previously mentioned,   according to gparted my sda1 is showing a content of 5.45GB in a partition of 25.8GB.   That's a lot bigger than simply filesystem overhead,  surely? 

> *Yes, you can.  If you have less than 1 gb of ram then you won't be able to install much, but you can certainly install a single small package like testdisk.*
You were right.  I have 1.25GB of ram and found that so long as I didn't do any browsing that puts stuff into cache,  I had enough spare to do an apt-get update on the Live CD's sources.list,  find testdisk,  and install it. 

I've now got some testdisk results which I'm attaching for an expert opinion.    

Find it's a bit heavy going,  running testdisk only from my Live CD because I can't save the testdisk installation there and would have to go through re-enabling 'universe' by editting sources.list and doing an apt-get update and getting and then installing testdisk if I want to run it again.   I notice there's a Windows version of testdisk available so do you see any snag if I install that in my Windows where I can save it and run it again much more readily.   That Windows is on my sda2 of the same sd so it should be able see my same partition table and sda1 details from there,  shouldn't it?       
> *Because resizing is going to move things around and likely overwrite more of any data that may still be there.  The bad geometry is because you changed the partition table and the fs contained in the now smaller partition still thinks it is the full size.  You need to repair the partition table and recover the fs, without doing the usual moving of files around that a resize normally entails.  That is where testdisk comes in.*
Right.  It makes more sense now that the data is still there on my HD but its location isn't matched by the entries in my partition table.  Clearly I'm going to need to get to grips with understanding all the parameters in partition tables before I do any more dabbling and am going to have to do some research on this.   Any guidance in this area of course would be most welcome.

Incidentally I notice that on testdisk's website cgsecurity.org there's another utility called PhotoRec which ignores the file system and goes after underlying data, so it can still work even if a media file system has been severely damaged or reformatted.   OTOH the files I'm hoping to recover are my /home and system files which probably wouldn't be so easily identifiable as pix or media files,  would they!

Since we've rather drifted off the original topic in this thread, d'you think it would be better if I start a new one to discuss partitioning and modifying a partition table?    I have to ask because I was chastised for starting this one when a previous one on Natty hibernation got stale.

---

### Post by psusi on 2011-08-10
Yep, you mucked up the partition table so it claims the ext4 partition is smaller than it is.  Testdisk seems to have detected the correct size, so have it repair it.

Then you need to fsck it.

---

### Post by Sleepy-zz-John on 2011-08-11
OK,  thanks again,  Attached are my preliminary fsck results.  Am taking it very cautiously here,  step-by-step,  and haven't pressed "y" on any of the fixit? prompts yet.   Still haven't got to grips with structure of cylinder, superblock. start and end point etc.,  but looks like fsck knows what it's doing better than I do!  Should I just cross my fingers and keep pressing "y" now?

Incidentally after that session of all "no" answers on fsck,  as I went in and opened my Win XP again, it gave me a prompt I've never seen before;  it had recognised changes to my computer since I originally registered that XP 5 years ago and required me to re-validate it.   Hard to believe that was just a coicidence and seems to indicate that despite all those no responses I gave,  fsck must still have saved something in the partition table.

---

### Post by psusi on 2011-08-11
You didn't have testdisk repair the partition table yet.

---

### Post by Sleepy-zz-John on 2011-08-11
Are you recommending testdisk as a preferable option to repair the partition table rather than e2fsck?    Both seem to have a repair capability, but I don't know which would be safer/easier/better.    There's even GParted as a 3rd option,  but again, no experience on relative merits.

If you're recommending testdisk,  then apart from general interest and gathering information,  I'm unclear what the point of the yesterday's fsck excercise was. 

I've now burned a Live CD of BootMed1 (basically a Live Maverick with testdisk and other partition-related utilities burned into it),  which I find is infinitely easier than struggling with trying to install testdisk working from my live Natty CD.   This Live Maverick seems a lot more stable and much less resource-hungry than my Live Natty.   I'm beginning to wonder if this might have some bearing on my original Natty hibernation troubles.

---

### Post by psusi on 2011-08-12
> **Sleepy-zz-John said:**
> Are you recommending testdisk as a preferable option to repair the partition table rather than e2fsck?    Both seem to have a repair capability, but I don't know which would be safer/easier/better.    There's even GParted as a 3rd option,  but again, no experience on relative merits.

e2fsck is for checking and repairing the ext2 series of filesystems.  It has nothing to do with partitions or partition tables.  Testdisk can repair partition tables.

> **Sleepy-zz-John said:**
> If you're recommending testdisk,  then apart from general interest and gathering information,  I'm unclear what the point of the yesterday's fsck excercise was. 

The point was to make sure that you didn't just have some minor filesystem damage that it would easily fix.  Instead it confirmed that the problem is with the partition table.

---

### Post by Sleepy-zz-John on 2011-08-14
> **psusi said:**
> You didn't have testdisk repair the partition table yet.
OK,  I'm now trying to do that using testdisk on a live BootMed CD

Encountering some difficulty in TestDisk (please see my attached "TestDisk.png") because when I highlight the 2nd entry there as shown in white,  and I then press Enter,   instead of analysing that (0,1,1) to (3464,254,63) partition it moves on to the next line,  Linux Swap,  shown there in green,  and asks me if I want to write to that,  which I don't. 

In an attempt to understand the structure of what I'm trying to do,  I've prepared a small spreadsheet from earlier details extracted from my partman log.  Not sure how much it can help,  but I'm attaching it here as "summary.ods",  anyway.  

I'm also attaching "Mount-error.png" showing the exact result I get when I try to mount sda1 on my live BootMed CD platform. This makes me wonder whether I'm trying to fix a partition table error or a file system error,  or both.

---

### Post by Sleepy-zz-John on 2011-08-14
Since my last posting,  I've discovered that TestDisk will only write table entries that are showing green,  so I've now been able to make some of the other lines green by changing them to show up as P for primary.  

But having re-written 4 lines into a new table,  the problem I have now seems to be that the sda numbers on my newly-written entries don't coincide with the sda numbers I had before.   Compare the numbers in my latest result "Write1-4.png" with the original sda numbers in "Summary.ods".  

Also I'm now missing the entry for the extended LBA part of my DATA that was originally on sda3.

So my questions now are:
   a) How do I write a new sda3 line into the currently saved table to match the original sda3 line I had?
  b) How do I edit TestDisk's currently saved sda3 line to make it show up as sda5,  and generally change the listing order so that all the sda numbers match their previous allocations?

---

### Post by wasteinc on 2011-09-09
I have the same problem with my swap file (after suspending, it gets full and then in random times it empties and then fills again)

I have 4GB of RAM and I certainly dont wont to use my swap. If I turn it off completely would this be wrong? I think it will save me a lot of trouble with suspending

---

