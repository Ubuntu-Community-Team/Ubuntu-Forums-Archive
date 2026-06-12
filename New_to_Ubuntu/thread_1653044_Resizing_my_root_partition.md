---
title: "Resizing my root partition"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by lightnin on 2010-12-26
Which is the best / safest way to resize my root partition without messing up my existing installation?


I have install/live CD's, but I thought it best to ask before I start messing about with partition sizes !

Thanks

Rich

---

### Post by davidmohammed on 2010-12-26
... first backup.  Dont do anything without a backup - I use clonezilla myself!

then

recommend you do the following :
1) Download and burn a GParted LiveCD (can get it from distrowatch.com)
2) Boot with the GParted LiveCD
3) Resize the appropriate Linux partition
4) When done, reboot, then boot into Ubuntu to be sure it still loads OK

---

### Post by laidback on 2010-12-26
You may well find Gparted, as supplied by Ubuntu, on your live CD. daidmohammed's idea is the better though particularly for the long term.

Gparted is VG.

---

### Post by lightnin on 2010-12-26
Thanks

I'll do a CD now then.

I backed up my Home folder last night, so I am set to go.

---

### Post by lightnin on 2010-12-26
Well, that worked ok.

It took a while .. I had to move all my partitions over to the right to expand my root partition.

Is that right ?  or is there a quicker shortcut ?

Thanks again

Rich

---

