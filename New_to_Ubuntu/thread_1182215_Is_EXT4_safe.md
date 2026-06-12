---
title: "Is EXT4 safe?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by MadsRH on 2009-06-08
During the 9.04 beta there were some ext4 bugs which could cause data loss. The bugs must be fixed by now (since ext4 will be default in 9.10), but is the bugs still there in 9.04?

I'm doing a reinstall and I would really like the ext4 speed, but not at the risk of loosing my data


Thanks for reading ):P

---

### Post by camper365 on 2009-06-08
I have yet to loose data caused by ext4 (I loose data doing other things though :)).
However, if you intend to use gfxboot, ext4 is not compatible with that.

If you are looking for absolute stability, I would stick with ext3, but if you are willing to sacrifice some comfort, go ahead with ext4.
However, as with any filesystem, you should always backup your data and avoid hitting the power button to turn your computer off, always do a clean shutdown, or use the magic sysRq key if you have to.

---

### Post by philinux on 2009-06-08
[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

---

### Post by Shibblet on 2009-06-08
> **camper365 said:**
> I have yet to loose data caused by ext4 (I loose data doing other things though :)).
However, if you intend to use gfxboot, ext4 is not compatible with that.

If you are looking for absolute stability, I would stick with ext3, but if you are willing to sacrifice some comfort, go ahead with ext4.
However, as with any filesystem, you should always backup your data and avoid hitting the power button to turn your computer off, always do a clean shutdown, or use the magic sysRq key if you have to.

That's a little scary to hear.  If EXT3 is stable, and EXT4 isn't, is it going to be stabilized and comfy by the 9.10 release?

---

### Post by MadsRH on 2009-06-08
> **camper365 said:**
> ...If you are looking for absolute stability, I would stick with ext3, but if you are willing to sacrifice some comfort, go ahead with ext4.

So you are saying that ext4 isn't stable yet?

---

### Post by handydan918 on 2009-06-08
> **MadsRH said:**
> So you are saying that ext4 isn't stable yet?

I'll go one better.

Ubuntu isn't "stable", either. 

No distro that rebuilds every 6 months can be described as "stable", in development terms.

---

### Post by rsambuca on 2009-06-08
> **handydan918 said:**
> I'll go one better.

Ubuntu isn't "stable", either. 

No distro that rebuilds every 6 months can be described as "stable", in development terms.

Oh, looks like the trolls are out tonight.

Ubuntu is considered stable.  So is ext4.

---

### Post by Wiebelhaus on 2009-06-08
A resounding _***YES!***_

---

### Post by lovinglinux on 2009-06-08
No problems here. 

There are already a few discussions about ext4 in the forums:

[Ext3 and Ext4: Which file system to install?](http://ubuntuforums.org/showthread.php?t=1133719)
[have you had any problems with ext4?](http://ubuntuforums.org/showthread.php?t=1170802)
[Should I switch to ext4?](http://wwww.ubuntuforums.org/showthread.php?t=1157658)
[Choosing ext4 over ext3](http://ubuntuforums.org/showthread.php?p=7209536)
[Jaunty and EXT4](http://ubuntuforums.org/showthread.php?t=1180097)

**Quick links to similar threads:** [Google Site Search](http://www.google.com/search?q=ext4+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) | [Forum Search](http://ubuntuforums.org/search.php?do=process&query=ext4)

---

### Post by mrbiggbrain on 2009-06-08
Ubuntu 9.10 uses a kernel that has the built in fixes for EXT4, thats not to say that EXT4 is unstable there is just an issue where becuse EXT4 writes data in a diffrent way...

with EXT3 theres always one version of the file, the old or the new, becuse of the improvements in speed of EXT4 sometimes there isnt a new or old version... EXT4 readys the space, removes the file, but dosnt write untill the program is actualy ready (a tiny ammount of time for things to go verry verry wrong.

the fixes sacrifice a little speed so that this issue dosnt happen nearly as often (like a few thousand times less often) but isnt in the kernel 9.04 uses, ju8st the one 9.10 uses... i guess you could recompile your own kernel, but with ubuntu...thats not really sujested.

---

### Post by H2SO_four on 2009-06-08
Yes :)

---

### Post by nandemonai on 2009-06-08
If you don't mind losing your data from an unexpected power outage or some such (hard lock) then maybe. Otherwise, stick to ext3. There is a reason it's not the default yet.

[http://ubuntuforums.org/showthread.php?t=1170123&highlight=ext4+data+loss](http://ubuntuforums.org/showthread.php?t=1170123&highlight=ext4+data+loss)

For example.

---

### Post by Bios Element on 2009-06-08
Yes, it's as safe as any file system can be without 30 years of testing. >.> And about 30% faster.

---

### Post by MadsRH on 2009-06-09
Thanks for all the replies. I will give EXT4 a try (and take a backup just in case).

[COLOR="YellowGreen"][SIZE="6"]Consider this thread solved[/SIZE][/COLOR] ):P

---

### Post by handydan918 on 2009-06-09
> **rsambuca said:**
> Oh, looks like the trolls are out tonight.

Ubuntu is considered stable.  So is ext4.

By whom? 
Poor form to call someone a troll when you offer nothing more than an ex cathedra statement for support.
Ubuntu isn't considered stable by anyone conversant with [Debian development terminology]("http://www.debian.org/releases/"). 
FYI, "stable" in this context has nothing to do with the system crashing or not crashing.


):P

---

### Post by Bios Element on 2009-06-09
> **handydan918 said:**
> By whom? 
Poor form to call someone a troll when you offer nothing more than an ex cathedra statement for support.
Ubuntu isn't considered stable by anyone conversant with [Debian development terminology]("http://www.debian.org/releases/"). 
FYI, "stable" in this context has nothing to do with the system crashing or not crashing.


):P

And FYI, "Stable" in this question was crashing/not crashing. The average user doesn't care about debian dev terms. They care if it's going to work or not.

---

### Post by Zeikcied on 2009-06-09
I've only had one instance of data loss, but it wasn't anything major.

Though I have had quite a few hard locks.  Most of which have been related to Dolphin (the KDE4 file manager) moving or deleting large files (like several hundred megabytes in size).  This morning I woke up to my system in a hard lock that seemed to stem from Akregator (I ended up having to delete its cache to get it to start again after I rebooted the system).

So, assuming these are ext4 related bugs, and not just regular bugs in Jaunty, it seems like not all programs are playing nice with the new file system.  But I think it's definitely something that will improve over time, now that distros are starting to support ext4, and especially with the next Ubuntu version making it the default file system.

---

### Post by rsambuca on 2009-06-10
> **handydan918 said:**
> By whom? 
Poor form to call someone a troll when you offer nothing more than an ex cathedra statement for support.
Ubuntu isn't considered stable by anyone conversant with [Debian development terminology]("http://www.debian.org/releases/"). 
FYI, "stable" in this context has nothing to do with the system crashing or not crashing.


):P

Of course your statement might have some actual meaning if the discussion were about Debian.  We are quite aware that ubuntu is based on the debian unstable branch, where snapshots are taken every six months, worked on, patched, made as stable as possible, and released.  This is all irrelevant to whether ext4 is stable or not, which is what the OP had asked.

---

