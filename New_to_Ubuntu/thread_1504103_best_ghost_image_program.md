---
title: "best ghost image program"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by idrinkwhisky on 2010-06-07
Hi,

i was wondering what the easiest ghost image program is for ubuntu. I see the names of clonezilla and partimage pop up here and there. What would you suggest?

Thanks

---

### Post by khelben1979 on 2010-06-07
[Clonezilla]("http://en.wikipedia.org/wiki/Clonezilla"). :)

---

### Post by djbushido on 2010-06-07
I've personally had quite a bit of success with PING - Partimage Is Not Ghost.
Just pick one and try, see what you like!

---

### Post by nhasian on 2010-06-07
+1 for clonezilla

---

### Post by idrinkwhisky on 2010-06-07
thanks. i ll look into both ping and clonezilla more. 

any chance future version of ubuntu will have it built in by default?

---

### Post by djbushido on 2010-06-07
It's really impossible to build that kind of software into an operating system - you can't have the system accessing the files while you're trying to copy them. PING and Clonezilla work on block-level access (very low-level file access), and trying to use these devices while something else is accessing them screws it up. Sorry, that's a horrible explanation, but I'm not exactly sure how to explain block-level devices.
Basically, it is impossible to build PING into an operating system to back up the system that's running it.
However, you can install PING (that I know of, not sure on Clonezilla) and make backups of other drives. I'm not exactly sure where i found it, I'll continue looking and report back.

---

### Post by CharlesA on 2010-06-07
I don't think that PING can deal with EXT4 file systems. Clonezilla can, however.

---

### Post by Locke_99GS on 2010-06-07
```
dd
```
That is all.

---

### Post by Paddy Landau on 2010-06-08
> **Locke_99GS said:**
> ```
dd
```That is all.
For laypeople (like myself), it's easier to use CloneZilla.

Does dd compress data and save only used blocks as CloneZilla does? I've never used it.

CloneZilla also saves the MBR, though I've never had cause to restore it so I don't know how that works.

---

### Post by nhasian on 2010-06-08
i swapped the 120gig HD that came in my laptop for a 500gig drive and clonezilla made it really painless.  it kept the windows partitions, linux partitions, master boot record, everything!  as long as you are moving from a smaller HD to the same size or bigger it is just fine.  I read that it doesnt work if trying to move to a smaller drive...

> **Paddy Landau said:**
> CloneZilla also saves the MBR, though I've never had cause to restore it so I don't know how that works.

---

### Post by Locke_99GS on 2010-06-08
> **Paddy Landau said:**
> For laypeople (like myself), it's easier to use CloneZilla.

Does dd compress data and save only used blocks as CloneZilla does? I've never used it.

CloneZilla also saves the MBR, though I've never had cause to restore it so I don't know how that works.

dd can do byte-by-byte or whatever block size you want, and you can pipe through other utilities such as gzip, a differencer, or whatever, and save to another device or to a file.  dclfdd is a more advanced version of dd.

Other utilities are probably much easier (and perhaps even better) but much (most?) of what they do can be done with dd, if you're feeling a bit geeky.

I use it mostly for cloning and zeroing out a salvage drive before use.

---

### Post by beew on 2010-06-08
Can PING or CloneZilla create images for only those portions in the partition that are actually used instead of imaging the whole partition? I mean, let's say I have Ubuntu on a partition that is 80G but I actually use only 8G (this is actually the situation now, Linux is unbelievably small!) how big the image would be?

---

### Post by Paddy Landau on 2010-06-08
> **nhasian said:**
>  I read that it doesnt work if trying to move to a smaller drive...
It doesn't. I tried!

---

### Post by Paddy Landau on 2010-06-08
> **beew said:**
> Can PING or CloneZilla create images for only those portions in the partition that are actually used instead of imaging the whole partition?
I don't know about PING, but CloneZilla copies only the used portions, and furthermore compresses the backup.

So, CloneZilla would save your 80Gb drive in less than 8Gb.

With CloneZilla, you can choose to back up a single partition, a set of partitions, or the entire disk. It's a little clunky, so it takes some getting used to, but I've found it amazingly reliable.

---

