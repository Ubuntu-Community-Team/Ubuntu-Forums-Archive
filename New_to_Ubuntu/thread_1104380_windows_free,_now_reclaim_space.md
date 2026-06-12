---
title: "windows free, now reclaim space"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by hollowtd on 2009-03-23
I have I think 3-4 gig missing since I cleared off the windows (It's a 20 gig hd but says I only have 14.7 for ubuntu). Is there a way to get this 3 or so gig for ubuntu now? cheers

---

### Post by kanikilu on 2009-03-23
You should be able to boot with the live CD, then run gparted to  delete the Windows partition (if it's still there) and then resize your Ubuntu partition to use that free space.

It should resize non-destructively, but always make sure you have a current backup of important data whenever resizing or doing anything with partitions.

---

### Post by Proteusiq on 2009-03-23
Have you being Using Ubuntu before? If Yes, Dive in it(If Your are ready) Complete Install Ubuntu...with no window partition!(I think If you reboot with the Ubuntu CD on, then you can install it)

I tend to use use all Disk,(it becomes faster) but I have not prove this yet!

---

### Post by hollowtd on 2009-03-23
So, I've already taken windows off. It's gone now. It seems that it only allows me to the 14.7 gig with the other 3 gig sort of unallocated. Is this how I would go back into gparted with running the live cd and somehow add this 3 gig to the Ubuntu partition? I mean here's how it looks. One bar showing unallocated 3.4 gig. Another bar showing 14.7 gig for ubuntu. Another small bar that says something about switch. (I'd just like to add the 3 or so gig to the ubuntu gig for a total of 18.- gig. It doesn't seem that I can do it as it's been previously partitioned. Sorry a bit confusing I know.

---

### Post by amadeus266 on 2009-03-23
You're on the right track, load the ubuntu cd and resize the Ubuntu partition. I don't remember if gparted will run from the cd or only when installing.

---

### Post by hollowtd on 2009-03-23
Great I'll give it a try. I think I have to put the live cd in in order to run gparted or at least resize the ubuntu partition.

---

### Post by theozzlives on 2009-03-23
Just resize it.

---

