---
title: "Upgrading"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-12
I will soon be getting a new machine with Ubuntu 8.10 preinstalled (a Dell Inspiron 15).

I'd like to upgrade it to 9.04.  And here's the real "duhhhh . . . " question:  How do I do that?

The answer in my mind is in one of those clouds where I can almost see it, but not quite.

---

### Post by gardara on 2009-08-12
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by mapes12 on 2009-08-12
If it's a new machine then I guess you won't have any critical data on it. Therefore, I would burn a fresh 9.04 installation disk and install from that. This will also give you an opportunity to set up your partitions so that future upgrades will not be so intensive.

---

### Post by BobJam on 2009-08-12
@mapes12,

I was thinking of doing just that . . . especially since I'm sure it will have a lot of the usual Dell crapware on it.

So I can use the 9.04 LiveCD to do my partitions too?  I'll have a 250GB HDD, what would you recommend?  I do like to have a separate partition for my data, and I'm sure I'll wipe out the useless Dell recovery partition . . . but what about the size for root and home, and the swap I assume will be sized as my memory (4GB) . . . though I don't anticipate using hybernation any.

Seems like there's some useful information on that very thing in this thread:  [http://ubuntuforums.org/showthread.php?t=1236742](http://ubuntuforums.org/showthread.php?t=1236742) on about pages 4 and 5.

---

### Post by BobJam on 2009-08-12
Oh . . . forgot to mention.  I also plan to create a VM for installing Windows XP.  Would that be a consideration in sizing the partitions?  (Not creating them, but sizing them).

---

### Post by zvacet on 2009-08-12
> So I can use the 9.04 LiveCD to do my partitions too?

Yes it can.From thread you provided link I see it is recommended to make root ( / ) 50 GB.I think it is to much for root.I will go for 10 ( it is enough but you can give 15 if you want).You can keep your data on home but if you want you can create another partition for that.Size will depends of your needs.If you want to install VM you can go for Virtual box.You can install it where you want to but I think home will be good choice( you want your data partition for data only and you don´t need to add to the root things you can put somewhere else.

EDIT: You can also use [Gparted live CD]("http://gparted.sourceforge.net/") for partitioning.

---

### Post by BobJam on 2009-08-12
> **zvacet said:**
> EDIT: You can also use [Gparted live CD]("http://gparted.sourceforge.net/") for partitioning.Is Gparted in the 9.04 LiveCD, or do I have to use the Gparted LiveCD separately?

Actually. now that I think of it, having installed 9.04 once (several months ago now . . . back when I fled Windows), it does do the partitioning right at the install anyway (gparted?).  I remember that slider and "Manual" option.

I have a tutorial for that somewhere . . . will have to go back and read over it before I start.  I think that's also in the link you provided, gardara.  Maybe they're all one and the same.

Bottom line, I think I have enough material (also have that Ubuntu Pocket Guide) to do the install and partitioning.

Thanks all.

---

### Post by Paqman on 2009-08-12
> **BobJam said:**
> Oh . . . forgot to mention.  I also plan to create a VM for installing Windows XP.  Would that be a consideration in sizing the partitions?  (Not creating them, but sizing them).

Yes. Your VM files are located in your home folder, so make sure that if you're putting /home on a separate partition that you allow enough room for the VM.

---

### Post by mapes12 on 2009-08-12
> Actually. now that I think of it, having installed 9.04 once (several months ago now . . . back when I fled Windows),and
> Oh . . . forgot to mention. I also plan to create a VM for installing Windows XP.What configuration are you looking for :confused:

---

