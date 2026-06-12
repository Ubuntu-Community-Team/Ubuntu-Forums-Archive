---
title: "Scared to resize partitions"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by stuffnsuch on 2009-09-17
:(
Hi, it's me again;
I have received lots of help from my previous "Help" post and now I have to enlarge my ubuntu partition. Maybe I have read toooooo  much about this process, but now I am worried about trying it, and losing my windows (yuk) vista OS. I have installed ubuntu in dual boot method.
For one I can't seem to get my system to boot from the disk I downloaded from ubuntu and the repartition program in (yuk) Vista doesn't want to let me enlarge my partitions.
My computer came preloaded, so I don't have a startup disk if all fails.
Yes I have done a major backup.
What is the best way to go about this, cause as you can see I sure would like to get away from (yuk) Vista.
Thanks;
Dan

---

### Post by tomBorgia on 2009-09-17
Hi Dan,

Have you burned the Ubuntu disk "as an image" or just copied the .iso file across?

You mention Vista won't let you ENLARGE your partitions... You can't have larger partitions than the physical disk size... you generally SHRINK the Vista partition then create a new one in the space left...

Sorry if that's what you meant anyway... I've no idea why Vista wouldn't let you shrink partitions...

---

### Post by vantsochev on 2009-09-17
Hi, well if it's really shrink, not enlarge, you will have to move the page file, which is located on the NTFS partition, you can use this:

[http://technet.microsoft.com/en-us/sysinternals/bb897426.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897426.aspx)

---

### Post by EssexEagle on 2009-09-17
> **vantsochev said:**
> Hi, well if it's really shrink, not enlarge, you will have to move the page file, which is located on the NTFS partition, you can use this:

[http://technet.microsoft.com/en-us/sysinternals/bb897426.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897426.aspx)

I also find that I can't shrink the Vista partition (well, I can, but not nearly as much as I'd like to), because of files which the Windows defragmenter can't move on the disk.

The PageDefrag page doesn't say it's compatible with Vista, and [this thread]("http://forum.sysinternals.com/forum_posts.asp?TID=10755") suggests it doesn't work well.

---

### Post by vantsochev on 2009-09-17
Sorry forgot twas Vista... Try this one:

[http://www.auslogics.com/en/software/disk-defrag/download](http://www.auslogics.com/en/software/disk-defrag/download)

or find some other page defragmenter tool for Vista... 

Then defragment your Windows drive and try to shrink it...

---

### Post by Bartender on 2009-09-17
If vista came pre-loaded there should be a utility somewhere on that computer to burn recovery DVD's.  Until you have made those you shouldn't be doing things that could wipe out vista.

Build a GParted LiveCD (link below) for partitioning.  Not for partitioning vista, but for working with the other partitions.

---

### Post by bodyharvester on 2009-09-17
you could go to one of those microsoft question/answer sites and tell them you want to shrink your Vista partition to make room for windows 7 and im sure theyll help you shrink Vista then :p

---

### Post by LewRockwell on 2009-09-17
> **Bartender said:**
> **_*If vista came pre-loaded there should be a utility somewhere on that computer to burn recovery DVD's.  Until you have made those you shouldn't be doing things that could wipe out vista.**_*

this, This, THIS!

.

---

### Post by LewRockwell on 2009-09-17
> **bodyharvester said:**
> you could go to one of those microsoft question/answer sites and tell them you want to shrink your Vista partition to make room for windows 7 and im sure theyll help you shrink Vista then :p

hahaha!

so true!

.

---

### Post by EssexEagle on 2009-09-17
This is a nightmare - I tried removing the hibernation file and all restore points, disabling the system restore, disabling virtual memory, disabling debugging information, disabling hibernation, deleting my page file, and then running four separate defragmenters (Auslogics, Power Defragmenter, Perfect Disk and O&O Defrag) and I STILL can't shift the files which are preventing me from shrinking the Vista partition any further!
(n.b. If you do try disabling the things I mentioned above, as is suggested [here]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"), be sure to re-enable them afterwards!)

> **bodyharvester said:**
> you could go to one of those microsoft question/answer sites and tell them you want to shrink your Vista partition to make room for windows 7 and im sure theyll help you shrink Vista then :p

It's beginning to look like this is the only answer!

---

### Post by LewRockwell on 2009-09-17
> **EssexEagle said:**
> This is a nightmare - I tried removing the hibernation file and all restore points, disabling the system restore, disabling virtual memory, disabling debugging information, disabling hibernation, deleting my page file, and then running four separate defragmenters (Auslogics, Power Defragmenter, Perfect Disk and O&O Defrag) and I STILL can't shift the files which are preventing me from shrinking the Vista partition any further!

check this out:

[http://itsfood.wordpress.com/2008/01/30/tech-how-to-defrag-in-windows-vista/](http://itsfood.wordpress.com/2008/01/30/tech-how-to-defrag-in-windows-vista/)

.

---

### Post by drs305 on 2009-09-17
Once you have reduced the size of the Windows partition this guide may help you in expanding the size of your Ubuntu system partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

I initially wrote it to help users who ended up with a very small / partition after a "side by side" installation with Windows, but the techniques apply to enlarging any system partition.

---

### Post by LewRockwell on 2009-09-17
[http://forums.cnet.com/5208-6138_102-0.html?threadID=331058](http://forums.cnet.com/5208-6138_102-0.html?threadID=331058)

.

---

### Post by stuffnsuch on 2009-09-19
Well,,, I got the partitions fixed and ubuntu worked fine but windows didn't so I had to restore windows and lost a lot of information (had a complete backup) now I have lost Ubuntu and it won't reload from the disk, so now I am downloading another copy to try.
Wish me luck,,,

---

### Post by EssexEagle on 2009-09-21
FWIW I'll add that I managed to fix the problem of Vista refusing to shrink, even after I'd disabled a load of stuff and defragged the disk.  The trick was to use [PerfectDisk]("http://www.perfectdisk.com/products/home-perfectdisk10-home-edition/free-trial") and to run an Offline Defrag (you have to reboot, and it defrags system files before Vista has completely booted up, when they're still movable).

Now I can shrink Vista loads... Ubuntu installation here I come :)

---

