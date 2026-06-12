---
title: "Merging free space at the beginning of an extended partition to the end of the primar"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by babajc on 2009-07-15
So, I freed up some space from the first partition in the extended partition of a hard drive, and so I now have about 1G unallocated at the start of it.  I'd like to grow the primary partition by utilizing this unallocated space.  gparted doesn't seem to do this.  Is there a way to do so??

Thanks for any and all help!

---

### Post by AndThenWhat on 2009-07-16
Gparted does do it. When you mess with partitions you should probably boot into the LiveCD. Then go into Gparted and turn off all of your swap partitions (swapoff option when you right-click). Then you can just drag the black arrows to exand/grow the partition:

[http://manual.sidux.com/lib/images-en/gparted-en/gparted05-en.png](http://manual.sidux.com/lib/images-en/gparted-en/gparted05-en.png)

Hope that helps.

---

### Post by CatKiller on 2009-07-16
Don't forget that you'll need to shrink the extended partition (the box around the other partitions) if you want the unallocated space inside it to be available for other primary partitions.

---

### Post by babajc on 2009-07-18
Thanks!  Will make an attempt shortly!

---

### Post by babajc on 2009-07-18
Those instructions worked PERFECTLY!  Thanks!

---

### Post by donaldt on 2009-07-20
> **AndThenWhat said:**
> Gparted does do it. When you mess with partitions you should probably boot into the LiveCD. Then go into Gparted and turn off all of your swap partitions (swapoff option when you right-click). Then you can just drag the black arrows to exand/grow the partition:

[http://manual.sidux.com/lib/images-en/gparted-en/gparted05-en.png](http://manual.sidux.com/lib/images-en/gparted-en/gparted05-en.png)

Hope that helps.

OK.  what if you don't have a "live CD".  What is a live CD, is it one that is not dead?  Or do you mean a ubuntu install CD?

I found out how to turn off the swap partitions, but without a CD I still have no access to the Gparted partitioning capability.  Do you have any other suggestions?

Thanks...

---

### Post by CatKiller on 2009-07-20
> **donaldt said:**
> OK.  what if you don't have a "live CD".  What is a live CD, is it one that is not dead?  Or do you mean a ubuntu install CD?

A [live cd]("http://en.wikipedia.org/wiki/Live_cd") is one that is able to run an operating system from the cd itself, without having to install anything. The Ubuntu install cd is a live cd, although there is a [GParted live cd]("http://gparted.sourceforge.net/livecd.php") too.

---

