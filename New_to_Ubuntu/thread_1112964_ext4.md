---
title: "ext4"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by expatCM on 2009-04-01
Confusion reigns ........  I am just wondering what happens when I upgrade to Ubuntu 9.04.

I guess I will do a fresh install, there are some fundamental changes so perhaps this would be wise rather than simply click the button to upgrade.  But ... what about the file system.

I am told that ext4 is more stable, faster and safer, lots of good reasons to use it.  But I am also told that GRUB does not support it.... yet.  Is that right?

I have a system with a data drive. That is ext3 at present.  I understand that I can upgrade the file system and the data is not trashed.  But I also understand that only new data attracts the new journaling system used by ext4.  Would that therefore not mean that it is best to make all data new data by formatting the drive and then copying it all back?  Or did I miss the point?

---

### Post by ssam on 2009-04-01
if you upgrade to 9.04 nothing will change automatically. 9.04 will have support for ext4 (grub and other tools has been updated to work with ext4). if you reinstall 9.04 you can choose ext4. it is possible from the command line to convert ext3 (or even ext2) to ext4, but as you say you will not get all the benefits, without doing a backup, and clean format.

it is likely that 9.10 with have ext4 as the default for new installs, and i imagine some future version with automatically convert ext3 to ext4 (the ext2 to ext3 migration where handled like this several years ago).

ext4 has been tested heavily by developers, and early adopters, but issues where found by 9.04 testers (ext4 is more likely than ext3 to loose data after an unclean shutdown in certain cases. these cases can be quite common with some common desktop software). this has been worked around for 9.04, but it is possible more issues will be found as more people use it.

ubuntu will usually aim for safe defaults.

[http://lwn.net/](http://lwn.net/) has several articles in the last couple of weeks about ext4.

---

### Post by alphacrucis2 on 2009-04-01
> **expatCM said:**
> Confusion reigns ........  I am just wondering what happens when I upgrade to Ubuntu 9.04.

I guess I will do a fresh install, there are some fundamental changes so perhaps this would be wise rather than simply click the button to upgrade.  But ... what about the file system.

I am told that ext4 is more stable, faster and safer, lots of good reasons to use it.


No, yes and no respectively. Ext4 is definitely speedier but it be a bold person who would claim that it is either more stable, or safer than ext3 at this point. The problems are being sorted out though.

>   But I am also told that GRUB does not support it.... yet.  Is that right?

No. The current version of Grub in the beta version of Jaunty does work with an ext4 boot partition. I think grub was recently patched to achieve this. My test machine that I upgraded the file system to ext4 after upgrading from alpha6 to the first beta only has ext4 partitions now and GRUB boots fine.

> I have a system with a data drive. That is ext3 at present.  I understand that I can upgrade the file system and the data is not trashed.  But I also understand that only new data attracts the new journaling system used by ext4.  Would that therefore not mean that it is best to make all data new data by formatting the drive and then copying it all back?  Or did I miss the point?

ext4 seems to be noticeably faster for me without rewriting existing files. Not sure about the journaling.

---

### Post by expatCM on 2009-04-02
hmmm ... well thanks for your information ....  good reading :)   I guess the one thing that slightly concerns me is the comments about loss of data on unclean shutdown.

The obvious approach is to shutdown carefully but I know in practice that the big power button is sometimes the only way to go ......  

But again, if I think about this in context, this simply means loss of the data in running applications rather than the corruption of a file system so perhaps it should not be a concern.

---

### Post by skymera on 2009-04-02
I run Ubuntu 9.04 with EXT4.

I have the journalling as data writeback and my system boots in 17 seconds (Bootcharted) 

I've had no problems, so i'd say it's stable and safe :)

---

### Post by binbash on 2009-04-02
grub is patched for ext4 no worries about that.But you may see data loss on ext4 which i had 2 days ago and had to reinstall the whole system!

---

### Post by expatCM on 2009-04-02
binbash .....  if I may ask, how, more or less, did you manage to totally trash the file system.  Were you playing with fire, running normally and had an unexpected event or say had to kill the power and found a headache on reboot?

---

### Post by philinux on 2009-04-02
For ext4 data loss read this article. Very self explanatory.

[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

---

### Post by Sef on 2009-04-02
Ext4 is in testing stage now.   It may work fine, but then you may have problems with it.  If you have an extra computer, then I would install it.   I would not recommend installing it on work computers at this time.

---

### Post by binbash on 2009-04-02
> **expatCM said:**
> binbash .....  if I may ask, how, more or less, did you manage to totally trash the file system.  Were you playing with fire, running normally and had an unexpected event or say had to kill the power and found a headache on reboot?


I did a clean shutdown, and when i open the pc grub gives an error which i can't fix it (did reinstall grub etc) BUT filesystem is not corrupted for sure because i can reach the files from live cd etc.

---

### Post by expatCM on 2009-04-02
I took a look at the article.  It seems that a fix for the problem is identified but it will not reach the world until kernel 2.6.30 or later.  The kernel in 9.04 is 2.6.28.

The problem occurs if there is activity in the last minute before the system shuts down / ends.  This would explain quite neatly why if you have a crash there can be subsequent problems.

To move forward then I guess the points of note are -

1. A solution exists.  It will be deployed at some near future time.

2. Keeping data and/or /home on a separate partition may be good practice.

3. Perhaps keeping an image of the installed o/s which is updated automatically each day would save a bit of irritation if there was a crash.

If this is all about write delays then I guess waiting a minute before shutting down could help until the fix is deployed........

---

### Post by alphacrucis2 on 2009-04-02
> **expatCM said:**
> I took a look at the article.  It seems that a fix for the problem is identified but it will not reach the world until kernel 2.6.30 or later.  The kernel in 9.04 is 2.6.28.

The problem occurs if there is activity in the last minute before the system shuts down / ends.  This would explain quite neatly why if you have a crash there can be subsequent problems.

To move forward then I guess the points of note are -

1. A solution exists.  It will be deployed at some near future time.



Actually I read it slightly different. The 2.6.30 version will include what Ted Tso refers to as "The proper" solution. But it sounds like he made a patch available as an interim workaround to make ext4 behave like ext3 in this regard. So I would say we want to know what kernel has this interim patch. Or am I wrong?


Yep I am wrong. I hadn't read the launchpad bug. It seems the workaround patch will get into 2.6.30

---

