---
title: "Copying a CD"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by newport_j on 2010-05-14
How does one make a copy of a CD in Ubuntu. The obvious and painful way is to copy the source CD's contents to the hard drive and then burn those contents onto a new blank CD. 

But, there must be a better way. An easier way - I mean.

newport_j

---

### Post by cascade9 on 2010-05-14
No idea how to do it Brasero, but K3B has a 'copy medium' option- you just pick that, and it wil automatically take an image of the disc, then burn it to a new blank disc.

---

### Post by sisco311 on 2010-05-14
Applications -> Sound & Video -> Brasero Disc Burner -> Disc copy

---

### Post by ajgreeny on 2010-05-14
If you only have one CD drive there is no way you can escape the business of copying the disk contents onto the hard drive and then writing back to a new blank CD.  Using brasero will, however make a temporary disk image unless you specifically ask it to copy to an image that you can burn later.

If you have two CD drives, Brasero will copy from disk to disk for you as you can choose the source and destination drives at start of the copy disk dialog of Brasero.

---

### Post by tica vun on 2010-05-14
```
#dd if=/dev/sr0 of=/path/to/image.iso
```

---

### Post by Tholley on 2010-05-14
I have never found Brasero to work for me. As well as allot of others... 
[http://ubuntuforums.org/showthread.php?t=1158979&highlight=BRASERO+SUX](http://ubuntuforums.org/showthread.php?t=1158979&highlight=BRASERO+SUX)
 
I usually use DeVeDe to copy as iso, then K3B to burn iso to new disc.

---

