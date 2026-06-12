---
title: "Disk reader not reading"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by icyest on 2009-01-03
I have VirtualBox running XP. I happen to have an "Office Student and Teacher Edition 2003" disk with the serial and everything. My virtual Machine (even though it's mounting using host cd drive) wont read the disk when I insert the disk.

How can I get it working?

---

### Post by Rolcol on 2009-01-03
I've only used disk images with VirtualBox.  What I would do if I had your problem would be to create a disk image and then mount that.

```
dd if=/dev/scd0 of=~/Desktop/office.iso
```

---

### Post by icyest on 2009-01-03
is it really legal to  take an Image file from the disk?

---

### Post by Rolcol on 2009-01-03
Well... you're paying for the software license.  If you already have a license, it shouldn't be a problem.  I don't think it's illegal to download a movie if you already have paid for a license but destroyed the disk.

---

### Post by Paqman on 2009-01-03
> **icyest said:**
> is it really legal to  take an Image file from the disk?

Depends. In the UK it's legal to make one backup copy of any software you own, and an image is a form of backup. This kind of thing varies a lot depending on where you are, though.

---

