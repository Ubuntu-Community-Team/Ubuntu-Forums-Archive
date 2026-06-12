---
title: "does Linux need a defrager?"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by s1baker on 2010-11-25
Does Linux need to be defraged every so often like XP?
I have deleted a ton of files and was wondering if there would be holes in the file structure that need to be compacted.

My system:
Ubuntu 10.10 32 bit with AMD 64 chip

---

### Post by Enigmapond on 2010-11-25
No it doesn't. Linux handles data differently than NTFS or FAT. You don't have data spread all over the place like you do in Windows. Every 20-30 boots, it will run a check disk just to check for errors. This is the only thing it needs to do.

---

### Post by A_M_S on 2010-11-25
Usually no.For more info read [this]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

---

### Post by d3v1150m471c on 2010-11-25
No, because of the way linux systems write to a disk, so enjoy it! A lesser known fact, for the best performance of your pc you shouldn't use more than half of your harddrive's space on any operating system. If you think about it like a suitcase, it's easy to initially pack stuff in to take with you on your trip but when you fill up 90% of it and try to fit your hygiene kit and a couple pairs of shoes...well, you have to totally reorganize and you run into problems.

---

### Post by bodhi.zazen on 2010-11-25
FYI: There is some low level fraqmentation present on all file systems.

I have not seen more then 5% on any of my Linux file systems.

It is possible to have significant fragmentation if your hard drive is very full.

Typically fragmentation needs to reach at least 40% to afect performance.

I have seen fragmentation on FAT and NTFS partitions as high as 800 %.

So while there is some low level fragmentation, it does not affect performance.

I mention this because some people seem to take the low level fragmentation too seriously :p

---

### Post by s1baker on 2010-11-25
thanks all.
that pretty much answered that

---

### Post by d3v1150m471c on 2010-11-26
EDIT:
```

sudo fsck -n /dev/sda1

```

"...(0.5% non-contiguous)" That's after running ubuntu for a year on this laptop. Lookin' pretty sweet to me

---

### Post by Dark7man on 2010-11-26
I was just about to post a thread on the same subject... I had read before that Linux OS does not need any defrag software, I wanted to ask though, does this apply to Ext HDD also, that would be accessed and read/write to via Ubuntu + Windoze?

If so, any software known to defrag ext. hdd from Ubuntu? (Goal being-to optimize and make use of Ubuntus non fragmenting file system)

OR if I keep my data movement to ext.hdd from within Ubuntu this will rule fragmentation out?
:popcorn:

Just something I was wondering about... Might helps others get better understand as well as myself! 

Thanks in advance for any info!

---

### Post by bodhi.zazen on 2010-11-26
> **Dark7man said:**
> I was just about to post a thread on the same subject... I had read before that Linux OS does not need any defrag software, I wanted to ask though, does this apply to Ext HDD also, that would be accessed and read/write to via Ubuntu + Windoze?

If so, any software known to defrag ext. hdd from Ubuntu? (Goal being-to optimize and make use of Ubuntus non fragmenting file system)

OR if I keep my data movement to ext.hdd from within Ubuntu this will rule fragmentation out?
:popcorn:

Just something I was wondering about... Might helps others get better understand as well as myself! 

Thanks in advance for any info!

It depends on the file system, both for the ard drive and removable devices.

FAT and NTFS will require defragementation from time to time. I do not think there are Linux tools to do this, so defragment with Windows tools from time to time.

---

### Post by Paqman on 2010-11-26
> **Dark7man said:**
> does this apply to Ext HDD also, that would be accessed and read/write to via Ubuntu + Windoze?

If so, any software known to defrag ext. hdd from Ubuntu?

Your external drive is most likely formatted as FAT32, which does suffer from fragmentation quite badly. However, since it's just a data drive you won't be doing a lot of writes to it like you would if you were running an OS from the drive. I wouldn't worry too much about it. Defrag occasionally using Windows if you like.

Switching to NTFS on the external drive will also reduce fragmentation to the point you probably don't need to worry at all.

---

### Post by Dark7man on 2010-11-26
> **Paqman said:**
> Your external drive is most likely formatted as FAT32, which does suffer from fragmentation quite badly. However, since it's just a data drive you won't be doing a lot of writes to it like you would if you were running an OS from the drive. I wouldn't worry too much about it. Defrag occasionally using Windows if you like.

Switching to NTFS on the external drive will also reduce fragmentation to the point you probably don't need to worry at all.

Niiice :guitar:

Thanks for the info... so does that mean so to speak?

1.  If I copy files to my EXT.HDD from within Linux, will this reduce the risk of fragmentation?

2.  Or it doesn't matter what OS I use to write the files to my ext.hdd, it depends on the format type (ex. FAT32, NTFS) of the Ext.HDD which effects which way the data is handled?

This may seem silly question, what I'm trying to get my head around is, the fact that Linux has this great tech. that almost eliminates fragmentation, is there anyway to take advantage from it...  I'm guessing formatting the Ext.HDD in "Ext4" would make the drive unreadable in Windoze?

Thanks for being so patient, I'm just trying to get an understanding of everything...
And thanks for the info so far \\:D/

---

### Post by tolf242 on 2010-11-26
> **d3v1150m471c said:**
> EDIT:
```

sudo fsck -n /dev/sda1

```

"...(0.5% non-contiguous)" That's after running ubuntu for a year on this laptop. Lookin' pretty sweet to me

[SIZE="2"]Hi, I ran that code to see what was what, it came back 0.3% non-contiguous. It also came back with this...

/dev/sda1: ********** WARNING: Filesystem still has errors **********

Is this warning going to be a problem?

Many thanks Tolf242.[/SIZE]

---

### Post by bodhi.zazen on 2010-11-26
> **tolf242 said:**
> [SIZE="2"]Hi, I ran that code to see what was what, it came back 0.3% non-contiguous. It also came back with this...

/dev/sda1: ********** WARNING: Filesystem still has errors **********

Is this warning going to be a problem?

Many thanks Tolf242.[/SIZE]

No, fsck will check and repair your file system every 20 mounts (boots).

If you are still concerned, start a new thread and post (copy-paste) the entire warning message.

fsck should also be run from a live CD with the root partition unmounted.

---

### Post by matt_symes on 2010-11-26
l

---

### Post by tolf242 on 2010-11-26
> **bodhi.zazen said:**
> No, fsck will check and repair your file system every 20 mounts (boots).

If you are still concerned, start a new thread and post (copy-paste) the entire warning message.

fsck should also be run from a live CD with the root partition unmounted.[SIZE="2"]

I will wait and see if the warning is still present in a couple of weeks(ie 20 re-boots). 

Thank you for your help, Tolf242.[/SIZE]

---

### Post by Paqman on 2010-11-27
> **Dark7man said:**
> 
it doesn't matter what OS I use to write the files to my ext.hdd, it depends on the format type (ex. FAT32, NTFS)

Correct.

> 
I'm guessing formatting the Ext.HDD in "Ext4" would make the drive unreadable in Windoze?


Also correct. FAT and NTFS are the only file formats that both OSes can read and write to.

---

### Post by ssulaco on 2010-11-27
> **tolf242 said:**
> [SIZE="2"]

I will wait and see if the warning is still present in a couple of weeks(ie 20 re-boots). 

Thank you for your help, Tolf242.[/SIZE]
You can force a fsck with this command anytime you want
```
sudo touch /forcefsck
```then reboot 
or if you want to change the frequency of the fsck
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by Dark7man on 2010-11-28
Nice info guys! Thanks for taking the time to answer my questions :)

Have a better understand of everything now :)

Mucho Respect!
:guitar:

---

### Post by llawwehttam on 2010-11-28
> **tolf242 said:**
> [SIZE=2]

I will wait and see if the warning is still present in a couple of weeks(ie 20 re-boots). 

Thank you for your help, Tolf242.[/SIZE]

You could always use:

```
sudo shutdown -rF now
```

which reboots you machine and forces a disk check on reboot.

---

