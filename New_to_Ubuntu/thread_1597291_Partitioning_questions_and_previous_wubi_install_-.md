---
title: "Partitioning questions and previous wubi install - advice please"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by egervari on 2010-10-15
Hi, 

I've been running the 10.04 wubi installation for awhile, and I want to go linux half-way now. It's just so much faster, and I don't have a million backround processes causing my hard disk to go to 80-100% read/write for 10 minutes while windows boots up.

I am also sick of waiting 60+ seconds for the uninstallers to decide what they want to do before they even ask me if I want to uninstall it or not. And a lot of other things.

I want to take my 700gb drive and partition it into 2 drivers, preferably an even split. I still want to keep my windows installation for photoshop and the odd game or two.

I already have a dual-boot setup for wubi put on. Do I have to uninstall wubi first before attempting a real installation to use my non-windows partition?

Also, should I use gparted to split the partition from the current wubi installation? Or go with a windows-based one? I want safety, and I want it to work.

Any tips/advice would be appreciated. Basically, as an end-result, I want to have windows on one partition, and ubuntu on another not using any virtual disks or anything like that.

I also want my boot loader to look clean and just give me 2 choices... not have a faux choice form the old wubi installation.

---

### Post by ft-Orchard on 2010-10-15
I Should say, just try it... Just uninstall wubi and install Ubuntu. Partition your harddisk when installing ubuntu. Use windows partition type for Windows installation, use EXT2, 3 or 4 for Ubuntu. 

If the install went smooth, and you don't have other os'ses installed, you should have 2 or 3 choices in you bootloader.

---

### Post by cpmman on 2010-10-15
If you want to keep any existing Wubi files back them up first externally (USB stick, cd etc.)

Remove Wubi via the uninstall program.

CCleaner or similar your Windows.

Defrag Windows until it is clear of red lines - ignore the "does not need defragging" message.

Use Windows disc utility to shrink existing windows partition as required. (If all four primary partitions are in use create the backup DVDs {about 3} and delete the backup partition using windows before shrinking)

Load live CD and use Gparted to make the unused partition extended.

Gparted partitions as wanted within the extended partition(recommend / , /home , swap I leave enough spare to load next ubuntu release(s)).

Install from live cd specifying manually partitions.

Reboot as install requires.

Reboot again into Windows to allow it to chkdsk etc.

Reboot to ubuntu and copy in your saved files.

Good luck.

---

### Post by egervari on 2010-10-15
> **ft-Orchard said:**
> I Should say, just try it... Just uninstall wubi and install Ubuntu. Partition your harddisk when installing ubuntu. Use windows partition type for Windows installation, use EXT2, 3 or 4 for Ubuntu. 

If the install went smooth, and you don't have other os'ses installed, you should have 2 or 3 choices in you bootloader.

Well, I did try and use gparted to shrink the partition... it failed the simulation :( I didn't lose anything though.

I've got as much backed up as I can on my 500gb drive, but there's about 200 gb I cannot back up. It's all the most irrelevant stuff though, so if I lose it, oh well.

When I booted using the ubuntu cd, I didn't see any options to resize a partition - just edit the size with a value. I wasn't sure if this was a "safe" resize, or if I was just going to destroy everything... so I just quit and went into the live cd partion of the install. That's where I used gparted.

---

### Post by egervari on 2010-10-15
> **cpmman said:**
> If you want to keep any existing Wubi files back them up first externally (USB stick, cd etc.)

Remove Wubi via the uninstall program.

CCleaner or similar your Windows.

Defrag Windows until it is clear of red lines - ignore the "does not need defragging" message.

Use Windows disc utility to shrink existing windows partition as required. (If all four primary partitions are in use create the backup DVDs {about 3} and delete the backup partition using windows before shrinking)

Load live CD and use Gparted to make the unused partition extended.

Gparted partitions as wanted within the extended partition(recommend / , /home , swap I leave enough spare to load next ubuntu release(s)).

Install from live cd specifying manually partitions.

Reboot as install requires.

Reboot again into Windows to allow it to chkdsk etc.

Reboot to ubuntu and copy in your saved files.

Good luck.

Thanks for all this advice. Yeah, I backed up everything I could, and I also defragmented my hard drive as much as I could. I also ran ccleaner already as well.

I didn't know windows had a method for shrinking partitions. Interesting. That gives me another option because gparted wouldn't do it.

As for ext type... which is better, 2, 3 or 4? Is 4 the newest/best?

Also, why do you split up the /home and / into 2 different partitions? Couldn't that cause problems if I run out of space in one or the other? Isn't it better to just use 1? I can back up, so I'm not worried about preserving /home on new installations.

Thanks for all the tips. I will begin trying them at once.

---

### Post by cpmman on 2010-10-15
Gparted doesn't play well with Windows - use the Windows disc utility for windows partitioning.

edit: you got there before me.

set / to about 8 Gb leaves enough room for everything bar installing other flavours (lubuntu kubuntu etc.)

a separate /home preserves your settings for included packages and also your manual additions but if you are happy to re-install and set-up again by all means use just / and linux swap.

---

### Post by mastablasta on 2010-10-15
with 10.04 you could just (after uninstalling wubi)
 
1. defrag the disk
2. with windows disk manager make another partition on your disk (and not firmat it)
3. boot from linuxCD and start to install
4. choose to install on largest onnocupied free space.
 
should install it into the new partition you just created.
 
btw you didn't say what windows you are using.

---

### Post by egervari on 2010-10-15
Thanks again for all the tips. I'll be starting my windows shrink shortly ;)

I'm using Windows 7. I hope that doesn't change anything ;)

Is the default 10.04 swap space enough, or should I really customize everything?

So 

/ -> 8 gig
swap -> 2 gig? 4 gig?
/home -> the rest?

---

### Post by cpmman on 2010-10-15
That's how I did my Windows 7.

swap space should be 1.5 - 2 times your memory.

---

### Post by egervari on 2010-10-15
Okay, I have 4 gigs, so I'll make it 8 gig too then. I'm giving linux about 250 gig total, so they'll be plenty of space I would imagine.

Thanks for all the advice. I'll let you know how it goes in a few hours! ;)

---

### Post by nothingspecial on 2010-10-15
Swap space twice the size of RAM is from when 2gig was huge.

You don`t need an 8gig swap space. It won`t do any harm, it will just be a waste of storage.

---

### Post by egervari on 2010-10-15
Okay, I've spent a really time defragmenting my system (I dunno why I thought it was defragmented... pass 5 took forever, and it went all the way to pass 9). I did it one more time just to be sure.

Unfortunately, windows won't let me shrink the volume by 200-250gb. It will only let me shrink by 27gb. It's giving me some excuse about unmovable files. ARGH!

How can I fix this? Do I have to download a program to defrag when windows isn't loaded?

---

### Post by cpmman on 2010-10-15
Sorry I am not much help with windows utilities when they don't work.

Try this script and post the output back here enclosed in quote tags:

***_[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")_***

Hopefully someone with more knowledge/experience than I have will be along to interpret and give guidance.

---

### Post by egervari on 2010-10-15
Well, I'm defraging with O&O Defrag. It's reporting that there is 19% fragmentation. So much for Microsoft's defragmenter. It also has an option to defragment the locked files near the end of the freespace of the drive on boot up. I'm sure I can shrink it after I'm done all of this. ;)

---

### Post by egervari on 2010-10-15
Hrm, I now only have 0.14% fragmentation, and I managed to get rid of my hibernate file and I disabled my pagefile.sys in windows 7. I still only get about 30gb of shrink space. Like wow... the algorithm that Windows uses must be really bad.

I'm going to do a complete defrag. It'll push things more at the front. If this doesn't work, I guess I'm only going to have a 26-28gb installation.

---

### Post by cpmman on 2010-10-15
Try running the script link in my previous post from live cd so that we can see what your disc thinks it has.

---

### Post by egervari on 2010-10-16
Yay, I managed to get this to work ;)

Here's what I did:

I had to disable the pagefile.sys (virtual memory), turn off hibernate and get rid of the 4 gig hibernate file on my c:. I also removed all of my system restore points.

I also went through my AppData, my user directory and both my Program Files/Program Files (x86) and cleaned up all the crap that was laying around. You'd be surprised how bad uninstallers are. There was piles of leftover data from Cakewalk Sonar 7, 8 and 8.5, tons of crap from iTunes (after an uninstall) and a pile of other things. I probably saved 10GB at least from doing this. Probably 15GB.

I also had some big files (10GB+). Make sure to just delete them because these are hard/take forever to defragment... and they WILL conflict with how much you can shrink using Windows Disk Format utility.

After I did all of that, I got another defragment program called PerfectDisk 11. I told it to  "Consolidate Free Space". This took about 6-8 hours (I dunno, I was sleeping). This pushed every file to the beginning of the disk with no gaps. Maybe O&O defrag  would have done this too, but it reported 16 hours for the same  operation.

PerfectDisk also did a MUCH better job defragmenting the MBT, metadata  and other system files before Windows booted up, which was FANTASTIC. I  know this is not the point of this post, but windows boot time increased  by 1000% as a result of this defragment for me. It was like night and  day. Between doing this, getting rid of the hibernate file, and stopping SearchIndexer.exe from starting, Windows 7 actually ran FAST. Can you believe it? It was actually really good.

I also re-did ccleaner before the defrag.

I rebooted after the defrag, and finally Windows' disk format utility analyzed the disk and allowed me to shrink it by 155 GB, out of a possible 250GB. While I think it could have done a better job, this was far better than the 25 GB it was reporting before. So I went ahead with the Shrink. It only took about 10 minutes.

I am now running on ubuntu 10.10 with 8192MB for / (i set to primary), 4096 for swap space and the rest is for /home (I set to logical). Both disks are using ext4.

I'm guessing that everything is now resolved. I hope this post and my methods help others out. If you're having the same problem as me, be prepared to spend about a day cleaning up your windows, defragging and shrinking your drive.

**Lesson**: If you have a big drive and are using Windows, split up into 2 partitions for the hell of it, because the disadvantage of having 2 drives is next to none, but if you should want to get 2 partitions later, it is a major hassle. Make 2 partitions when you have a big drive!

---

### Post by cpmman on 2010-10-16
Good work well done.

Please use the thread tools at the top to mark this thread "SOLVED".

---

