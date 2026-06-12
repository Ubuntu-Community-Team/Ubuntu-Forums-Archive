---
title: "Making copies of Ubuntu Install CD"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by DayLite on 2010-09-03
I have my own copy of the Install to Ubuntu10.04. Now I want to burn copies for my friends.

Do I make copies from an iso or a data disk exact copy of my install disk that I used to boot Ubuntu.

---

### Post by cj.surrusco on 2010-09-03
I suppose you could do it either way, but the faster way would be to write the .iso to as many CDs as you want. It takes longer to read from a CD than to read the .iso from the hard drive.

---

### Post by DayLite on 2010-09-03
> **cj.surrusco said:**
> I suppose you could do it either way, but the faster way would be to write the .iso to as many CDs as you want. It takes longer to read from a CD than to read the .iso from the hard drive.

Thanks for responding so quickly :D

---

### Post by kroq-gar78 on 2010-09-03
if you don't have the iso file handy but you do have the disk, you can use a program called "dd" (preinstalled, I think) and output it to an iso file.

```
dd if=/dev/cdrom of=/tmp/cdimg.iso
```that's how you would do it.

---

### Post by DayLite on 2010-09-03
> **kroq-gar78 said:**
> if you don't have the iso file handy but you do have the disk, you can use a program called "dd" (preinstalled, I think) and output it to an iso file.

```
dd if=/dev/cdrom of=/tmp/cdimg.iso
```that's how you would do it.

Thanks, I have the ISO saved on my computer and I also burned the ISO to a disk, I also have the actual install CD that I used to install Ubuntu. So I am all set up ;)

---

### Post by jroa on 2010-09-03
Then just burn the iso just like you did for the install disk you have.  Should work fine.

---

### Post by DayLite on 2010-09-04
> **jroa said:**
> Then just burn the iso just like you did for the install disk you have.  Should work fine.

I burned the ISO and tomorrow I will mail the CD to my friend in Georgia.

Thank you for your help and support.

---

