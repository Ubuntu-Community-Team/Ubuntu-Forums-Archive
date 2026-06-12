---
title: "Problem with one of my partitions...."
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Kooz on 2009-06-22
Hi, I'm a new Ubuntu user, I'm extremely happy with it and I can't believe I waited to long to try it out, but I'm glad I'm using it now, I'm just begining to "feel" my laptops specs, since I used to have Windows Vista before(nasty).

Anyway, so I finally decided to delete my windows partition and so did I, now I formatted that partition to ext4, but I cannot seem to mount it from Ubuntu using gparted, so I tried with the bood cd to format it , but not only did it formart the partition but also installaing Ubuntu 9.04 again on the other partition, so now I had 2 partitions with 2 Ubuntu installed, I re-formart the partition again from Ubuntu hoping it would stay mounted, but I still can't use it. 

So in short, what I would like to know is
how to format that partition and mount it so I can store things there as well?


Also, I have another "partition"; which is about 10 gigs under the name TOSHIBA SYSTEM, should I also format that? Thanks in advance for the help. Cheers!

---

### Post by Sealbhach on 2009-06-22
Use gparted, the partition editor, rather than the Live CD (I assume that's how you ended up installing Ubuntu all over again). The only problem might be that your bootloader is now on that partition, so you might not be able to boot into Ubuntu if you reformat that partition.

That 10GB Toshiba system partition is probably your factory original recovery partition, if you ever want to restore our system to how it arrived (with Vista and bloatware), you use that partition to restore it.

.

---

### Post by Kooz on 2009-06-22
Well, I've tried booting that empty partition on gparted from ubuntu, and it seems it's fine and ready to use, but when I try to paste stuff it on it says I can't, then it figures as not mounted and I'm not able to mount it from gparted so I can use it.... I reformat it to ext4, flag as boot, apply and then I still can't use it cause it says it ain't mounted... Thanks for the help!

---

### Post by Sealbhach on 2009-06-22
OK, well have a look at this and see if it's any help:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

.

---

