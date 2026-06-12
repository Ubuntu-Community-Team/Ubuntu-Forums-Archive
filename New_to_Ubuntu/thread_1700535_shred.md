---
title: "shred"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by ZoeX on 2011-03-05
Hello

How make floppy ubuntu or other disro based  boot disk with shred command on it?
I have have to clean u old pc which does not boot from cdrom.

is shred already inside bash? 


thanks ZoeX

---

### Post by TeoBigusGeekus on 2011-03-05
You could take the hd off the old pc and attach it to another.

---

### Post by ZoeX on 2011-03-05
> **TeoBigusGeekus said:**
> You could take the hd off the old pc and attach it to another.

That's not my point, i have to clean data that no-one cannot recover it 
because laptop is old 1996, there is no way to boot from cd, bios does not have any option.
and floppy is attached for laptop via centronic port.

only what i need is shred program to make clean up.

is it inside bash? 
how to add shred for floppy.img image?
or it there already  image and bash with include it?


thanks ZoeX

---

### Post by Paqman on 2011-03-05
> **ZoeX said:**
> 
is shred already inside bash? 


No, on Ubuntu it's part of the package [secure-delete](apt:secure-delete).

If you want to boot off a floppy, you won't be able to do it with Ubuntu. You may be able to use one of the older versions of [DBAN]("http://sourceforge.net/projects/dban/files/dban/dban-1.0.7/"), which should fit on a floppy.

More info about DBAN: [http://www.dban.org/](http://www.dban.org/)

---

