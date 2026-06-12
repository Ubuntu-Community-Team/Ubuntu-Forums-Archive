---
title: "2 Hard Disks, which one?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by HomoGleek on 2009-10-24
Hi

My mother just bought a new netbook for the kids too use, its an MSI.

Its has 160GB space, but its split across 2 disks, in Win C: is called OS_Install (Its 40GB), while D: has no name.

I'm going too install Karmic on release, but my question is, does it matter which disk I install it on?

I will be giving it around 15GB space, there's enough on both too do that.

---

### Post by martrn on 2009-10-24
Hi Darren,

If you or someone else has a laptop or a netbook, usually these come with only one disk.  Usually they come with one disk split annoyingly into several partitions, but still usually they only have one disk.

If you have a 160GB disc space, then you need to install ubuntu to its own partition on that disc.  You will need to partition your hard drive into several partitions on your hard drive before you install ubuntu to one of your hard drives. Try not to use wubi.

You can get gparted from [/gparted.sourceforge.net/]("http://gparted.sourceforge.net/screenshots.php"). Which gives you a gui way of partitioning your hard drive first, although you can do this from a live ubuntu disc.

Partitions on ubuntu (or any unix/unix-like os) are called :

/dev/hda1    or  /hda1   [windoze calls this c]
/dev/hda2    or  /hda2   [windoze calls this d]
/dev/hda3    or  /hda3   [windoze calls this e]

If you have more than one hard disc the second disc with say on partion will carry on like this.

/dev/hdb1    or  /hdb1   [windowze calls this f]

You will see this adds clarity to the organisation of your hard disks becuase you never know in windowze if you have discs or partitons but you can tell easily at first glance in gnu/linux/ubuntu.

Make sure you defrag any windowze discs before you install ubuntu.

---

### Post by HomoGleek on 2009-10-24
I think I get that, One disk, but Win has got 2 partitions on it

Hopefully all goes well come next weeks release.

Thanks :)

---

### Post by clekstro on 2009-10-24
Hey Darren,

Just wanted to make sure you knew one more thing: if you see /dev/*sda1* instead of /dev/hda1, that is completely normal.

And if Grub asks you whether or not you would like to install it on the MBR partition, you can say >> yes <<.  Grub should pick up on the fact that you're running windows, at least i have had no problem with xp and vista.  does that laptop have vista or windows 7 on it?

---

### Post by HomoGleek on 2009-10-24
> **clekstro said:**
> Hey Darren,

Just wanted to make sure you knew one more thing: if you see /dev/*sda1* instead of /dev/hda1, that is completely normal.

And if Grub asks you whether or not you would like to install it on the MBR partition, you can say >> yes <<.  Grub should pick up on the fact that you're running windows, at least i have had no problem with xp and vista.  does that laptop have vista or windows 7 on it?
The netbook has XP currently

---

