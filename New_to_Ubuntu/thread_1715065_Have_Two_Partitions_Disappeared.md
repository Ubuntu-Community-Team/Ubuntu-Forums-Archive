---
title: "Have Two Partitions Disappeared?"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by Andavane on 2011-03-26
I'm referring to two dual-booting threads started earlier.
Here is the thread of case #1:
[http://ubuntuforums.org/showthread.php?t=1533756]("http://ubuntuforums.org/showthread.php?t=1533756")
where three partitions are shown. (copied out as I hadn't sussed windows screengrabs at the time).
In a nutshell, I settled on Wubi, on which I had a few issues, described here, case #2:
[http://ubuntuforums.org/showthread.php?t=1594498]("http://ubuntuforums.org/showthread.php?t=1594498")

The latest is that I now want to do Proper Dual-booting on this machine. Using Windows computer Management to shrink the partitions, I was astonished to find that two partitions appear to have gone, as in the attachment at the end of the post.

So I'm curious as to where the attachments have "Gone". My guess is that the other two (mentioned in first thread) were residuals or something, left for reverting to a previous windows OS, programmed to be removed after a certain length of time. Certainly it seems typical of Windows just to remove entire partitions without the owner's awareneness or permision. Or is this just bias or a flight of fancy?

Any comments welcome. 
Also any more tips on "Proper" Dual Booting Ubiuntu with Win-7 as opposed to using Wubi (which is just really meant to be a testing OS, nice though it is)

---

### Post by Mr Stoozer on 2011-03-26
I'm sorry to start the post in this manner but it's utter nonsense Windows' typical behaviour is just to delete entire partitions without the users consent.
You my find that if you split the "unallocated space" and try to leave the file system blank (ie leave it unformatted) it'll extend the partitions automatically so as to create one partition. (indeed typical behaviour) 
A way around this is to format the partitions to NTFS, boot Ubuntu and then format them to whatever you want at install time.
Also note that only 3-4 (not 100% sure) partitions can be created.

My advice would be to create an extended partition which works around that issue; with that 250GB partition (so it goes green) then split it into 2, one for OS (/) one for user data (/home)
Install ubuntu as normal.

I'll upload a screenshot of my diskmgmt.msc in a while as it's pretty much what you're looking for.

---

### Post by Mr Stoozer on 2011-03-26
OK, here's my diskmgmt.msc
 
A little explanation:
 
We're interested in the 1st HDD. As you see, it's been split several times.
Pre-Ubuntu I started by splitting the drive into 2: Windows & User_Data.
I then shrunk the Windows partition 30GB which left me with an extended partition (note the green). I then shrunk the 30GB ex. partition 20GB to leave me with 10GB for the OS, another 5GB for user data and another partition for testing. All partitions were initially formatted to NTFS (as otherwise it'll re-extend as noted previously)
 
Now, you may be looking at mine thinking why only the 15GB partition is extended. Well, the truth is, it's not. The 3 partitions in the middle (10GB 5GB & 15GB) are all part on one extended partition. I think becuse the first 2 are formatted an EXT4 Windows now has a spaz recognising what they are and only displays the 3rd as extended.
 
[ATTACH]187166[/ATTACH]
 
I hope this helps you out.
 
P.S  Have a Windows startup disk handy as if you knock out the bootloader and have issues during Ubuntu's installation, you'll have no Boot manager.
command to fix the Windows bootmanager if needed:
```
bootrec /fixmbr
```
if that fails
```
bootrec /fixboot
```

---

### Post by Andavane on 2011-03-26
> **Mr Stoozer said:**
> OK, here's my diskmgmt.msc
 
A little explanation:
 
We're interested in the 1st HDD. As you see, it's been split several times.
Pre-Ubuntu I started by splitting the drive into 2: Windows & User_Data.
I then shrunk the Windows partition 30GB which left me with an extended partition (note the green). I then shrunk the 30GB ex. partition 20GB to leave me with 10GB for the OS, another 5GB for user data and another partition for testing. All partitions were initially formatted to NTFS (as otherwise it'll re-extend as noted previously)
 
Now, you may be looking at mine thinking why only the 15GB partition is extended. Well, the truth is, it's not. The 3 partitions in the middle (10GB 5GB & 15GB) are all part on one extended partition. I think becuse the first 2 are formatted an EXT4 Windows now has a spaz recognising what they are and only displays the 3rd as extended.
 
[ATTACH]187166[/ATTACH]
 
I hope this helps you out.
 
P.S  Have a Windows startup disk handy as if you knock out the bootloader and have issues during Ubuntu's installation, you'll have no Boot manager.
command to fix the Windows bootmanager if needed:
```
bootrec /fixmbr
```
if that fails
```
bootrec /fixboot
```

Thanks - I'm studying your two posts.
This machine doesn't have a floppy but it does have an external cd drive you can boot from. Can I make a boot disk on cd? It must be so - I'll google this to investigate.

---

### Post by Andavane on 2011-03-26
mmm attempts to make recovery cd returned this (same with another cd):

---

### Post by oldfred on 2011-03-26
Be careful creating additional partitions in windows. It does not see Linux  partitions even though they are there. It may also convert to a logical volume SFS or Dynamic partitioning scheme which is compatible with nothing. Use windows tools for Windows & Linux tools for Linux.

The Ubuntu install CD is also a liveCD which you can & should run to test your system to make sure it works. It then can be used for repairs. Always have a working liveCD/liveUSB for every system you install. I like to have several as sometimes one works better than another for certain repairs.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Many of above are duplicates presented in slightly different ways, one may make more sense or after reviewing one the other may make more sense.

---

### Post by Mr Stoozer on 2011-03-26
> **oldfred said:**
> Be careful creating additional partitions in windows. It does not see Linux partitions even though they are there.
Negative.  Windows sees all partitions, it may not be able to tell what filesystem resides on the partition, but it sure knows it's there. Check my screenshot for confirmation.

---

### Post by Mr Stoozer on 2011-03-26
> **Andavane said:**
> Thanks - I'm studying your two posts.
This machine doesn't have a floppy but it does have an external cd drive you can boot from. Can I make a boot disk on cd? It must be so - I'll google this to investigate.
Sure you can make a boot CD, do it for both OS'.
If your PC supports booting from USB (and you have a spare 4GB laying around), that's the easiest option. If not, in Windows, install EasyBCD and force it to.
 
Also, by what means are you obtaining your recovery media?  OEM, MS Startup recovery?

---

### Post by Andavane on 2011-03-30
> **oldfred said:**
> Be careful creating additional partitions in windows. It does not see Linux  partitions even though they are there. It may also convert to a logical volume SFS or Dynamic partitioning scheme which is compatible with nothing. Use windows tools for Windows & Linux tools for Linux.

The Ubuntu install CD is also a liveCD which you can & should run to test your system to make sure it works. It then can be used for repairs. Always have a working liveCD/liveUSB for every system you install. I like to have several as sometimes one works better than another for certain repairs.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

...Many of above are duplicates presented in slightly different ways, one may make more sense or after reviewing one the other may make more sense.

Thanks. Had another good read. Little by little the partitioning lingo sinks/synchs in. One ideally would need two screens, I feel, one with the tutorial, one with the GParted Tutorial.

Anyway, it's all up-and-running nicely now (screenshot attached).

It turned out that there *was* another partition when I acquired the machine, a Vista bootloader that came with the machine. This made three partitions, one left for Ubuntu and I had nothing for the swap area. Hence my initial difficulties.

---

