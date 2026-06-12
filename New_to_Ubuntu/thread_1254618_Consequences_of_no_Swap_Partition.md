---
title: "Consequences of no Swap Partition"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by earthpigg on 2009-08-31
Hello,

machine i am putting together has 6gb of ddr3, and i am fairly sure i will never come close to using all of it.

because it has an SSD, i am considering not having a swap partition.

though i am fairly sure i will not be using up all 6gb any time soon, id like to know what will happen if all that space is used and i don't have a swap partition just for my peace of mind.

hard freeze?

i know it wouldn't he hard to test --- simply open firefox 5000 times with a zillion tabs each until something crazy happens --- that seems a bit drastic :lolflag:

---

### Post by jrox717 on 2009-08-31
Yep, pretty sure you would get a hard freeze. For a while I didn't have swap enabled (but I didn't know that I didn't) and I kept freezing up and couldn't even use the sys rq keys to reboot... Of course, I only have 512 MB of RAM. I'm pretty sure you'll be ok with 6 GB. 
Oh, and you can't hibernate without swap, though you can suspend.

---

### Post by t0p on 2009-08-31
My EeePC has a SSD of just 4GB (plus I have /home mounted on a 4GB sd card) so I've got Eeebuntu installed with no swap.  I get hard freezes sometimes.  But I've only got 512MB of RAM on that machine.  I intend to upgrade to 2GB, at which time I expect the freezes to stop.

With 6GB of RAM I shouldn't think you will have any problems.

---

### Post by credobyte on 2009-08-31
Your main post answered your own questions - it might ( in most cases, definitely ) freeze and screw something up. 512Mb of swap isn't that much .. allocate it & don't worry about how much space you have there - that's just the way it is :)

---

### Post by earthpigg on 2009-08-31
ok, i thought so. thanks guys!

my netbook only has 1gb and no swap, but i've always watched it because i was paranoid :D

---

### Post by QIII on 2009-08-31
If you plan to use the hibernate feature of your machine, your swap needs to be the same size (plus maybe 5% for good measure) as your total RAM.

RAM state is stored in your swap on hibernate.  If you have X GB of RAM and X/2 GB of swap, your RAM state can't be saved and you will likely get errors when you try to take your machine out of hibernate.

Windows does something similar, but I believe it dynamically sets the size of the disk space used to store the RAM state.

---

