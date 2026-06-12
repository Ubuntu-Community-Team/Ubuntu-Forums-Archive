---
title: "reinstall query"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by fronswa on 2008-12-09
Can anyone point me in the direction of some good sources for reinstalling ubuntu please? A wipe then a reinstall? 

I've went from 7.10 to 8.04 to 8.10. I've tinkered a little and at one point I accidentally transferred half the files from one place to another using an ftp client. Ho ho ho... I was totally stunned when everything still worked. 

I'm going to go for a fresh start and get everything set up the way I want it. The sound problem in firefox is doing my head in too. 

I'm going to get a few books on basic Linux principles, and put in a bit of effort to understand it more. 

PS
Do you still need to install CD or DVD drivers after a format of the HD? Back in the Win95 days I formatted my hard drive on 2 occasions, and my God... it just refused to run anything from the CD drive. Even after I loaded them from a floppy. 

Cheers

---

### Post by rev0lv3r on 2008-12-09
> **fronswa said:**
> Can anyone point me in the direction of some good sources for reinstalling ubuntu please? A wipe then a reinstall? 

I've went from 7.10 to 8.04 to 8.10. I've tinkered a little and at one point I accidentally transferred half the files from one place to another using an ftp client. Ho ho ho... I was totally stunned when everything still worked. 

I'm going to go for a fresh start and get everything set up the way I want it. The sound problem in firefox is doing my head in too. 

I'm going to get a few books on basic Linux principles, and put in a bit of effort to understand it more. 

PS
Do you still need to install CD or DVD drivers after a format of the HD? Back in the Win95 days I formatted my hard drive on 2 occasions, and my God... it just refused to run anything from the CD drive. Even after I loaded them from a floppy. 

Cheers

If you're just going to do a wipe and reinstall, this is what I would do

Download a 8.10 ISO
Burn it to a disc
Then insert disc into drive
Than just do a regular install, when it comes to the part where you have to partition, just destroy your old partitions and overwrite them.
Or you can use the LiveCD and use GParted to destroy them and recreate them however you want
This time you can take your time to learn the advantages and disadvantages of seperate partitions, different filesystems, etc.

---

### Post by handydan918 on 2008-12-09
> **fronswa said:**
> Can anyone point me in the direction of some good sources for reinstalling ubuntu please? A wipe then a reinstall? 
[/CODE]Really. all that is needed is to simply reinstall the version you want (8.04 I assume!)
[CODE]I've went from 7.10 to 8.04 to 8.10. I've tinkered a little and at one point I accidentally transferred half the files from one place to another using an ftp client. Ho ho ho... I was totally stunned when everything still worked. 

I'm going to go for a fresh start and get everything set up the way I want it. The sound problem in firefox is doing my head in too. 

I'm going to get a few books on basic Linux principles, and put in a bit of effort to understand it more. 

PS
Do you still need to install CD or DVD drivers after a format of the HD? Back in the Win95 days I formatted my hard drive on 2 occasions, and my God... it just refused to run anything from the CD drive. Even after I loaded them from a floppy. 

Cheers

No, the cd should just boot, with the occasional exception of some SATA cdroms.  If you have a weird issue like that, post back. There are workarounds, like installing from a flashdrive.

Still, I'm truly refreshed to hear from someone seasoned enough not to whine "Why isn't it easy like Windows?"
You can always tell someone who has never actually lived through a Windows install to tell the story. 


:rolleyes:

---

### Post by fronswa on 2008-12-10
Thanks for that. 
I was toying with doing a complete reinstall of windows as well - but life's painful enough as it is. I think I'll just stick to doing ubuntu - this time anyway. 

I noticed that I was able to access files that I had in windows - that's how I managed to bring over all the music that my friends had heaped on me (14Gb). 

I've tried to find it again so that I can put the music and other stuff back on windows to save it during the reinstall - can't find it now. 

Can you tell me what it's called? Somewhere in dev?

---

### Post by handydan918 on 2008-12-10
If you can post the output of ```
sudo fdisk -l
``` I'd be willing to bet that someone will be able to tell you exactly where to go to find your Nat King Cole collection (just kidding!)

:guitar:

As long as you haven't done any partitioning or deleting, it's likely all still there.

---

### Post by fronswa on 2008-12-10
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         166     1333363+  27  Unknown
/dev/sda2   *         167       36978   295692390    7  HPFS/NTFS
/dev/sda3           36979       60044   185277645   83  Linux
/dev/sda4           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

```
I removed the Disk ID just to be a over-cautious chap.

---

