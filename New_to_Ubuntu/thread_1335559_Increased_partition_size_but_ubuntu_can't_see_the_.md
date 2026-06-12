---
title: "Increased partition size but ubuntu can't see the extra space"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by G_Alexander on 2009-11-23
Hi

I have shrunk my Windows partition and increased my extended partition and then my main ubuntu partition. I have increased it from 32gb to 180gb. 

Oddly, gparted said straight away after the operation completed that there was only 2gb left on the now 180gb partition. From within ubuntu, if I right click Filesystem it still thinks the drive is 32gb. palimpest Disk Utility in the System > Administration menu correctly sees the partition as 180gb.

Is there another setting somewhere I need to change to allow ubuntu to use the extra space?


Many thanks
Grant

---

### Post by kansasnoob on 2009-11-23
Did you do the resizing using gparted from a live CD?

---

### Post by G_Alexander on 2009-11-23
> **kansasnoob said:**
> Did you do the resizing using gparted from a live CD?

Yes, I used a gparted live cd I downloaded from the gparted site. Thanks

---

### Post by G_Alexander on 2009-11-23
Got more disk space using "resize2fs /dev/sda5" from the live CD.

---

