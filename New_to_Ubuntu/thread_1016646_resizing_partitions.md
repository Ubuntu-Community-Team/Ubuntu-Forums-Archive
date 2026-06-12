---
title: "resizing partitions"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by blairm on 2008-12-20
Hi,

Recently set up a dual boot of Vista Home Premium 64 and Kubuntu Intrepid and miscalculated pretty badly - only allowed 60gb on a 320gb drive for linux. 
My music collection alone is almost 30gb, so can see there could be problems down the track.

Am I able to increase the size of my Kubuntu partition (probably to about 160gb) without messing up files in the existing Vista and Kubuntu installs? 
Or do I need to reinstall both of them from scratch?

Thanks,

Blair

---

### Post by shifty_powers on 2008-12-20
it is possible to do with the gparted livecd (google it).

but it is never without risk, so back up your data first!

if you don't please be aware of the (small) risk of data loss...

---

### Post by indytim on 2008-12-20
> Am I able to increase the size of my Kubuntu partition (probably to about 160gb) without messing up files in the existing Vista and Kubuntu installs?

Since you're going to be doing some partition work anyways, I'd suggest that you move your data type of stuff (music included) into it's own partition away from your ops.  That way you won't have to contend with loosing that data if you should ever install, re-install another version / ops in the same hd space.

You can achieve mounting of these new partition(s) by modifying your fstab.

IndyTim

---

### Post by Duck2006 on 2008-12-20
Resize the vista partition from with in vista with the partition tool.
Once that is done then resize the ubuntu partition with gparted or parted magic.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://partedmagic.com/](http://partedmagic.com/)

Some info on using gparted.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

---

### Post by hyper_ch on 2008-12-20
> **shifty_powers said:**
> so back up your data first!

one should always have backups...

---

### Post by mkvnmtr on 2008-12-20
Why would you resize the Vista partition from within Vista when you have the install disk with Gparted on it?  I made my Mac partition smaller last night with my Ubuntu live disk and it only took about 10 minutes. Would Vista be more reliable?

---

### Post by Duck2006 on 2008-12-20
> **mkvnmtr said:**
> Why would you resize the Vista partition from within Vista when you have the install disk with Gparted on it?  I made my Mac partition smaller last night with my Ubuntu live disk and it only took about 10 minutes. Would Vista be more reliable?

Because vista don't like to be partitioned with other partitioning tools other then it's own.

---

### Post by blairm on 2008-12-22
Thanks for the advice, everyone.

Unfortunately I decided to do it after a few drinks... must have picked the wrong option in Gparted and and lost my Vista partition (no great loss; new machine so there there was almost nothing on it to lose).

A piece of (probably unnecessary) advice: playing with partitions while under the influence is never a good idea:)

Blair

---

### Post by Zeedok on 2008-12-22
> **blairm said:**
> A piece of (probably unnecessary) advice: playing with partitions while under the influence is never a good idea:)

Some of us, and I include myself, learn this the hard way](*,)

---

### Post by Captain_tux on 2008-12-22
> **blairm said:**
> Unfortunately I decided to do it after a few drinks... 

Blair

Join the club! Vodka martini, anyone?!

---

### Post by mkvnmtr on 2008-12-22
I have found GParted pretty good a stopping me from doing the wrong thing but some of are good at fouling things up. Last night in using GParted I found a couple of tutorials on using it to work on Vista but it looks to me like Duck is right it is better to use Vista tools first and then do the rest of the disk with GParted.

---

