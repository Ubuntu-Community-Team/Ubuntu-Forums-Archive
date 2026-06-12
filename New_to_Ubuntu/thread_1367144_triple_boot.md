---
title: "triple boot"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by asnbd on 2009-12-29
hi,

how do i  make my imac triple boot with (mac, linux, & windows)?

any suggestion is appreciated

---

### Post by proxess on 2009-12-29
Usually grub works fine for this... or grub4dos.

---

### Post by neo.patrix on 2009-12-29
Grub can support multiple boot e.g. different linux-kernels with Windows. I guess Mac is not much different although I have never used it.

If you are asking how to make partitions etc. for that a more details about your hard-drive partitions is necessary.

Atleast two partitions are need for each OS in my experience, one to install your OS & programs , other for data, but data partition can be made common. 

Probably you will need two primary partitions one to install windows OS (c: drive) other for Mac. You can make all your Linux partitions (even root) on Extended Partition. So overall two primary & one extended are basic. I  guess for Windows XP 8-12 GB primary partition (c:) should be enough (if you are not planning on installing  high-graphics games). 4-5 GB for Linux Root (/).

---

### Post by FinalCoyote on 2009-12-29
> **asnbd said:**
> 

how do i  make my imac triple boot with (mac, linux, & windows)?



I thought that in order to run Windows on a Mac you had to use boot camp or something?

(I don't have a Mac, so don't take my word for it), but i thought it was a emu thing?

---

