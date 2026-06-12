---
title: "Clonezilla question"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by canam101 on 2009-09-23
I made an image of the two partitions, root and home, on my hard drive. Just in case, I also made an image of the entire hard drive, which was the same two partitions.

Then I put in a live disk and deleted the hard drive partitions.
Then I recreated them, but made the two partitions bigger than they had been (I had only used a small part of the available hard drive space when I installed the system originally).

Then I booted up with Clonezilla and restored the two partitions from the images of the partitions I had made a short time before.

I thought that this would have given me partitions with a lot of extra space but that did not happen.

Instead, the new, larger partitions, were even fuller than the old, smaller, original partitions had been.

Everything worked, but I did not get my extra space. I finally re-restored with the entire hard drive image and am back where I began.

Any idea what I can do to do it right if I try this again?

---

### Post by LewRockwell on 2009-09-23
is it possible that clonezilla saw the deleted but not erased previous data and wrote the imaged data back around the original data?

you might DBAN the drive and try again

we use clones and not images so that, if necessary, we can go straight to the cloned data(as opposed to the restrictions inherent in a compressed image)

.

---

### Post by nhasian on 2009-09-23
it is very common for people to image an old drive/partition and then install a newer larger hardisk to restore the image to.  

here's an example of how to clone a small disk to a larger disk:

[http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone](http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone)

---

### Post by LewRockwell on 2009-09-23
> **nhasian said:**
> it is very common for people to image an old drive/partition and then install a newer larger hardisk to restore the image to.  

here's an example of how to clone a small disk to a larger disk:

[http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone](http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone)

OP's trouble-call relates attempting to reuse the original hard drive in question after repartitioning in an attempt to change the size(s) of the operative partitions

.

---

### Post by howefield on 2009-09-23
> **canam101 said:**
> Any idea what I can do to do it right if I try this again?

"Try selecting the "Do not create partition in target hard disk in client" option from the advanced parameters listed while restoring the partition. If you forget, Clonezilla will resize the enlarged partition to the original size".

---

### Post by nhasian on 2009-09-23
oops your right.  if thats the case, why use clonezilla at all?  just resize the partitions with gparted from a LiveCD :)

> **LewRockwell said:**
> OP's trouble-call relates attempting to reuse the original hard drive in question after repartitioning in an attempt to change the size(s) of the operative partitions

---

### Post by LewRockwell on 2009-09-23
> **nhasian said:**
> oops your right.  if thats the case, why use clonezilla at all?  just resize the partitions with gparted from a LiveCD :)

in this particular instance your method might be employed

however...

since the original thread referenced the usage of clonezilla...

we were attempting to assist in it's effective employment/deployment...

.

---

### Post by canam101 on 2009-09-24
Thanks for the replies. I'll leave it as is for now, and give it another try when the remaining space dwindles a bit more.

---

