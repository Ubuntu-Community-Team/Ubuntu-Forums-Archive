---
title: "Dual Boot Repartition"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Mockingbird9 on 2010-05-13
OK, so I installed Karmic Koala and I set up a dual boot, since then I've used the windows partition twice.  So now that I am going to upgrade I thought it would be a good time to adjust those partitions - I was thinking of just getting rid of Windows but of course then someone hands me an Itunes giftcard...  so anyhow started looking up the easiest way to adjust, gparted doesn't let me adjust my windows partition so I was thinking it might be easiest to back up my files delete the linux partitions and then do a fresh install of Lynx and do the partition during installation.

Am I making this too complicated?  Better thoughts or will this work?

Thanks so much! :P

---

### Post by readycarpenter on 2010-05-13
so you only need to reinstall ubuntu? 

the easiest way, is to boot the live cd and delete the previous ubuntu partition, and reinstall there, grub will detect the windows os, and setup the same as you already are, 

or you could just upgrade your previous ubuntu using the update manager. here is a nice guide to do that [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

cheers

---

### Post by Mockingbird9 on 2010-05-13
Thanks, I'll try that - I couldn't tell from the upgrade notes if that would let me change the partition size.

---

### Post by readycarpenter on 2010-05-13
I didnt realize you were asking about resizing your partitions, 

the best way if you need to resize your windows partition, to use gparted, to shrink it, then after you shrink you windows partition, then you can expand your ubuntu partition, 

gparted is the tool, located under system> admin> "partition editor" on the live cd, you can also run from your current ubuntu, but can only resize/shrink/expand partitions not in use, but should let you shrink you windows partition, 

also gparted only comes on the live cd, to install run 

```
sudo apt-get install gparted 
```

or search for gparted in the package manager
cheers

---

