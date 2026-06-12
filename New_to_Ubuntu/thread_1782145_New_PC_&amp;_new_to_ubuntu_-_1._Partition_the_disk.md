---
title: "New PC &amp; new to ubuntu - 1. Partition the disk?"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Ace..... on 2011-06-14
Over the night of June 8/9 2011 my laptop failed. somebody told me they`d seen warnings on the news re: PC`s and the solar flare (due to hit the planet over this same period).
Was the flare responsible?
I`ve never seen a failure like this - only "eSystems" (the logo) appeared on screen  - but no bios - hard disk perfect (phew).

The new laptop:
Acer emachines E644 - AMD 2 Core C-50
3Gb DDR3 mem
500 Gb hard drive

Pre-installed: Win 7 home premium

**Q 1. What are the ideal partitions for ubuntu?**

eg. For XP I used to have C for Win; D: Programs; E: Data; F: Swap G: Browser cache

Note: Perhaps like most noobs, due to lack of ubuntu knowledge, I took a punt on my partitions & install method:
I switched off Restore Points, deleted all previous RP data, shrunk C: to
C: Win7 @ 49 Gb ............. D was pre allocated to DVD so created:
E: ubuntu @ 49 Gb ............ around 400 Gb remains unallocated.

Used "install ubuntu alongside windows"

Using Nautilus file explorer, I found that E was now called "File System" with only 9 Gb free????
I checked each folder, finally discovering that folder host (within E:File System) has 35 Gb free.

Have I screwed up?
Is the 35Gb effectively lost?
Should I delete partition E: and then re-partition & re install ubuntu?
Should I try shrinking partition E?
What are the ideal partitions for ubuntu, its progs, data, and caches etc?

This begs the Q: how best to organise the files, but perhaps that is so tied up in this thread, it will fall out under discussion.
:p

---

### Post by jerome1232 on 2011-06-14
1. No solar flares do not cause laptops to fry



2. How did you install, did you pop the disc and run an installer from within windows or did you pop in the disc, reboot, then run an installer?

3. You didn't need to pre-partition, Ubuntu's Installer can take care of that automatically, if you have only one big partition, Ubuntu's installer can automatically shrink it and install itself along side windows.


Do get more details about your current setup, can you post the output of fdisk from within ubuntu? Just open a terminal (alt+f2, type gnome-terminal, hit enter) use ctrl+shift+c to copy the output of of gnome-terminal.

```
sudo fdisk -l
```

---

### Post by jerrrys on 2011-06-14
open a terminal and enter **df**

what does that tell you?

---

### Post by Ace..... on 2011-06-14
Thanks for the replies. :p

The install was from a download using win explorer.
ie.got the pc up and running and logged on, searched for linux, saw ubuntu, and downloaded what I believe was simply an installer.
It said it would place it on C: but i figured they thought alot of people would ONLY have C.
I presumed, rightly or wrongly, it would be best to place it in its own partition.
sadly, it was all just guesswork, hence my thread, to establish what is the best filing system.

Here is the output:


fdisk:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6d88933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1959    15728640   27  Unknown
/dev/sda2   *        1959        1972      102400    7  HPFS/NTFS
/dev/sda3            1972        8307    50888704    7  HPFS/NTFS
/dev/sda4            8307       60802   421664768    f  W95 Ext'd (LBA)
/dev/sda5            8307       14681    51200000    7  HPFS/NTFS
/dev/sda6           14681       20928    50176000    7  HPFS/NTFS
/dev/sda7           20928       22203    10240000    7  HPFS/NTFS

df:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0            12844976   3081296   9111188  26% /
none                   1397080       696   1396384   1% /dev
none                   1404788       200   1404588   1% /dev/shm
none                   1404788       100   1404688   1% /var/run
none                   1404788         0   1404788   0% /var/lock
/dev/sda5             51199996  14118004  37081992  28% /host
/dev/sr0               4584512     52048   4532464   2% /media/UDF Volume
/dev/sda3             50888700  27100656  23788044  54% /media/eMachines
/dev/sda6             50175996     89340  50086656   1% /media/Data

---

### Post by wildmanne39 on 2011-06-14
Hi, it looks like you installed it with wubi which is through windows, is that what you did and is that what you meant to do? I am going to give you some links to look at, you need to read a little before you install.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) Some of the guides are all about partitions. One has pictures. It is best to resize your partition in windows to make room for ubuntu.

---

### Post by jerome1232 on 2011-06-14
To further elaborate there are two installers that come on an Ubuntu installation disc, one, known as Wubi, is meant to try Ubuntu out without having to mess with partitions, It installs Ubuntu onto a virtual filesystem which exists as a large file on your Windows partition. This is the method you used.


To get a true dual boot with it's own parition you would firstly want to remove the wubi install you have, you can do this from your add/remove programs (or whatever they call it now) interface from within windows.

You would then want to create unallocated space for ubuntu on your disk, then reboot your computer with the cd-rom in your machine.

You should be put into the standard installer which will offer to allow you to install Ubuntu as a true dual boot. Details about that should be provided in those links posted earlier.

Should you choose to manually partition just keep in mind Ubuntu needs at least a / partition, and a small swap partition is highly recommended.

---

### Post by nzjethro on 2011-06-14
> **Ace..... said:**
> 
Pre-installed: Win 7 home premium

**Q 1. What are the ideal partitions for ubuntu?**

...

This begs the Q: how best to organise the files, but perhaps that is so tied up in this thread, it will fall out under discussion.
:p

Are you wanting to keep Win 7 installed? If so, I would recommend 1 partition for Win 7 (or it may try to keep 2 - one for "System Reserved") one for Ubuntu, and one for shared data (that's the setup I have). I wouldn't bother with a separate /swap partition, just create a swap file ([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)). If possible (i.e. if Win doesn't have 2 partitions, or if you don't want  to keep Win, or if you want to have your shared data as a logical partition), chuck an unallocated extended partition in there, which you can create logical drives in to try other distros or test releases down the track.

---

### Post by Ace..... on 2011-06-15
Thanks for the v useful responses
@[wildmanne39 ]("http://ubuntuforums.org/member.php?u=508533")
Yes I used wubi.
It may be causing a [90178.637429] general protection fault 0000 [#1] smp
2nd line ended in /shared_cpu_map
further down it talked about "emachines 644" (my win7 partition)

The reading list you supplied was 1st class

@[jerome1232]("http://ubuntuforums.org/member.php?u=453029")
as above....... yes, sadly I need to start again with add/remove.
Clearly I need to create a cd rom ubuntu install disk, hopefully a simple task.
You disagree with [nzjethro]("http://ubuntuforums.org/member.php?u=1306925") re partitioning for a swap file.
My original intention was to create a separate swap partition, but I guess i can do that later as i have 3Gb ram.

@[nzjethro]("http://ubuntuforums.org/member.php?u=1306925")
Yes i want to keep win7 for a number of reasons.
Primarily cos i then have a fallback position, but also cos im gonna have to start to reinstate data and may need windows.
I will use win7 partitioner cos win7 effectively owns the disk, and cos ubuntu can install into a logical partition (great!)

So i will not touch the small reserved partition.... win7 is already shrunk.

@all
Does 50Gb logical 1st partition sound good (for ubuntu)?
this will leave around 400Gb for data/swap/cache partitions.

So i need to decide on a version 64bit or 32bit.
The 32bit is recommended at  [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
here is a 32 v 64 doc: [http://zone.ni.com/devzone/cda/tut/p/id/5709](http://zone.ni.com/devzone/cda/tut/p/id/5709)

It suggests that the primary gain is "breaking the 4Gb ram ceiling"

I did a search in these forums and found this thread (that is current now).
[64 bit: current experience]("http://ubuntuforums.org/showthread.php?t=1783026&highlight=32bit+64bit")

So it is confusing.
do you think Ubuntu, is playing safe, with the 32bit reccomendation?
Or are there real negative issues with the 64 bit?

(just editing this having read response from [[COLOR=#339900]**tgm4883**[/COLOR]]("http://ubuntuforums.org/member.php?u=191664") on above thread)

he is a grand java chip ubuntu member....... sounds (and surely is) impressive.
His advice was to install 64bit.
yeah.......lets do that.

---

### Post by mips on 2011-06-15
> **Ace..... said:**
> 
So i need to decide on a version 64bit or 32bit.
The 32bit is recommended at  [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
here is a 32 v 64 doc: [http://zone.ni.com/devzone/cda/tut/p/id/5709](http://zone.ni.com/devzone/cda/tut/p/id/5709)

It suggests that the primary gain is "breaking the 4Gb ram ceiling"

I did a search in these forums and found this thread (that is current now).
[64 bit: current experience]("http://ubuntuforums.org/showthread.php?t=1783026&highlight=32bit+64bit")

So it is confusing.
do you think Ubuntu, is playing safe, with the 32bit reccomendation?
Or are there real negative issues with the 64 bit?

(just editing this having read response from [[COLOR=#339900]**tgm4883**[/COLOR]]("http://ubuntuforums.org/member.php?u=191664") on above thread)

he is a grand java chip ubuntu member....... sounds (and surely is) impressive.
His advice was to install 64bit.
yeah.......lets do that.

Go 64-bit, your questions have been answered in that other thread.

---

### Post by jerome1232 on 2011-06-15
> **mips said:**
> Go 64-bit..

+1.

The only exception is if your one of those unlucky few who need a specific proprietary app which is not compatible with 64 bit.

In nearly all cases 64 bit is backwards compatible with 32 bit stuff.

---

### Post by Ace..... on 2011-06-15
I think i should be ok there.
The missus uses facebook - and that works
my son uses spotify and youttube.
youtube works with the flash helper app
dont know about spotify, but theyve just started charging for music, so havent been on for a while
other than that it is normal work apps, which seem to be included

oh yes, my email is Pegasus - just checked and they dont list a linux version.
bummer cos it has a great "self learning spam" module.

maybe ubuntu has something comparable.

I just tried to find where evolution stores my mail (before deleting the os).
couldnt find it......... couldnt find any mention of it.

I must be too tired.
tomorrow is another day!

thanks everybody so far.

---

### Post by wildmanne39 on 2011-06-15
> **Ace..... said:**
> I think i should be ok there.
The missus uses facebook - and that works
my son uses spotify and youttube.
youtube works with the flash helper app
dont know about spotify, but theyve just started charging for music, so havent been on for a while
other than that it is normal work apps, which seem to be included

oh yes, my email is Pegasus - just checked and they dont list a linux version.
bummer cos it has a great "self learning spam" module.

maybe ubuntu has something comparable.

I just tried to find where evolution stores my mail (before deleting the os).
couldnt find it......... couldnt find any mention of it.

I must be too tired.
tomorrow is another day!

thanks everybody so far.
Hi, your welcome and I have been using 64 bit for four years and I have not had any problems.

---

### Post by jerome1232 on 2011-06-16
> **Ace..... said:**
> 
I just tried to find where evolution stores my mail (before deleting the os).
couldnt find it......... couldnt find any mention of it.

.

If you want to backup your evolution settings, Click File->Backup up Evolution Settings.

This will backup all profile settings and mail.

edit: The only reason I encourage a swap partition rather than a swap file is well your new to this and it's easier. Most people use a swap partition, so it's more standard. There is however nothing wrong with using a swap file.

---

### Post by Ace..... on 2011-06-16
Hello chaps
I've deleted wubi ubunto, deleted the partitions, and loaded ubuntu from cd.

I expanded win7 partition to 100Gb leaving the rest unallocated, thinking the space would be split...but no.
Win7 partition has now got 100+ Gb.
ubuntu has got 376Gb ext4(?) + a linux swap partition of 2.9Gb

Note: there is now a PQ service 16Gb NTFS partition + system reserved 105 Mb + Win7 105Gb NTFS + 376Gb ext4 + 2.9Gb Swap
 
Not the end of the world, cos i read that ubuntu doesn't worry about start points, so i guess i can shrink back win7 partition, and move ubuntu partition left (if you see what i mean)

however............
1st prog i opened was  disk utility.
I clicked on the extended 379Gb extended (ubuntu) partition, and it said:

WARNING:the partition is misaligned by 1024 bytes - may result in v poor performance - repartitioning is suggested.

No panic, but........
...what's to be done.

I surely need to shrink win7 (C: in old money), but is this mis alignment a concern?

Here is the data prev requested:

sudo fdisk -l:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6d88933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1959    15728640   27  Unknown
/dev/sda2   *        1959        1972      102400    7  HPFS/NTFS
/dev/sda3            1972       14681   102088704    7  HPFS/NTFS
/dev/sda4           14681       60802   370463745    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5           14681       60446   367602688   83  Linux
/dev/sda6           60446       60802     2860032   82  Linux swap / Solaris
mark@mark-eME644:~$ 

df:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            361834044   3238096 340215816   1% /
none                   1397076       688   1396388   1% /dev
none                   1404788       112   1404676   1% /dev/shm
none                   1404788       100   1404688   1% /var/run
none                   1404788         0   1404788   0% /var/lock
/dev/sda3            102088700  30352796  71735904  30% /media/Win7
/dev/sda2               102396     24704     77692  25% /media/SYSTEM RESERVED
mark@mark-eME644:~$ 


what do you think my next step should be?

---

### Post by nothingspecial on 2011-06-16
Hello Mark,

By the way, before I start, just because I have a lot of posts, don't for one minute think that I know the first thing about partition alignment, because I don't.

I'm 99.99% sure however that you are not at risk from data loss because of it.

And I pretty sure that because it is the extended partition that is misaligned it doesn't matter anyway......

.... but like I say, I don't really know what I'm talking about.

Rather than spending time worrying about it, I'd make a new  thread about the alignment issue, and get on messing about with Ubuntu until someone who does know about it comes along to advise you about it.

---

### Post by Ace..... on 2011-06-16
yes,
i posted, poured myself glass of wine, and reflected.......thought that maybe a new thread was in order.

but it opens up a number of issues:

1. this is a disk partitioning thread - and clearly my disk has been partitioned.
2. if i'm being warned about a prob post installation, then this should perhaps be alerted to the guys who program the installation app.
3. perhaps a new thread is required, but.....which forum is correct for this thread.

on the latter, i'm just thinking that a lot of noobs would not necessarily first check their disk management software after an install - though also perhaps they should be alerted to do so.

for myself, my main objective is to primarily establish a good filing system, before pushing ahead with rebuilding my data.

just like my first install (that was wrong), i need to know this one is fundamentally correct - then i can move forward. ;)

---

### Post by nothingspecial on 2011-06-16
The point is, that your thread looks like a new user looking for advice on how to partition for install.....

....which it is.

Now, this is a huge place. There are users here who may know a great deal about your new issue. But may not bother reading this thread because of the title.

Look at this

[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Your problem exactly, and answered be someone who knows exactly what s/he's talking about.

Luckily for me, it kind of backs up what I was saying.....

.... but my point is, you've got to tailor your title for the right expertise, if you see what I mean.

I just happened upon your thread, a more specific title is more likely to attract someone who knows how to solve your issue.

---

### Post by Ace..... on 2011-06-16
Yes... it's all true.
The forum method is a humungus mish mash of repeated, and half repeated questions and answers... but it works, and is definitely better than the 5 year plans that are FAQ's.

Sometimes you need somebody to step in and point out a thread that answers your question (did that myself for someone just this week).
Thankfully you've done that for me (thanks for that).

It looks as though this could be a reporting error in the disk management software.

not a small issue IMHO, cos it screws up efficiency (wild goose chases).

anyway, if this is the case, then I'm nearly there.
just gotta shrink windows back (again).

but.......another Q......... what is this PQ service partition that has just appeared (16Gb - a bit costly no)?

in my reading up, I thought I'd learned that windows doesn't like having it's start point moved.
hmmm.... I'll just quit out and see if windows boots.

just editing.....forgot to agree with you on "creating the right title".
I try to remember to search a forum before posting a Q, and am often amazed at the duff titles given to a question (that relates to a prob I'm having).

surely, i should have started a new thread.... i guess it just goes to show that we are all prone to error.
:)

---

### Post by Ace..... on 2011-06-16
Well - windows runs.

checked out the partitions created for me by ubuntu installer.

not really over the moon...... one expert in the earlier reading list links, stated that linux should not be given a primary partition, cos it doesn't need it (waste of a primary partition).

thing is: ubuntu installer (according to win7 partition manager), not only placed ubuntu in a primary partition, but it also created another primary partition for the swap file.

Windows can't even see these volumes, so it's stretching the imagination a bit when it (installer) says it will install ubuntu alongside windows, and sharing data seems out of question.

I shrunk the win7 partition back, but couldn't expand or move the ubuntu volume, so i've got 50Gb unallocated between win7 and ubuntu volumes.

Then I found that my broadband speeds in ubuntu are around 25% slower than in win7 - did around 7 tests in both os's - pretty stable results for each.

Looks like i need to start a couple of new threads now (tomorrow is a better idea). :-|

---

