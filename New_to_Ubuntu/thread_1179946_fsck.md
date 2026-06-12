---
title: "fsck"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by DarinB on 2009-06-06
how do i run fsck for a certain hard drive in jaunty and will it reset my mount count to 0

---

### Post by philinux on 2009-06-06
fsck needs to be run on unmounted file systems or damage may occur. 

Best run from the livecd or from recovery mode. From recovery.

fsck /dev/sdaX

---

### Post by whoop on 2009-06-06
if you fear the command line you can also run partition editor from the livecd right click on a partition and select check.

---

### Post by DarinB on 2009-06-06
recovery mode sounds good how would i do that
I mean which choice do choose from the boot menu forward

---

### Post by mirons on 2009-06-06
If you're running fsck just for resetting mount count you can use this command to set mount count to 0
```
sudo tune2fs /dev/yourdisk -C 0
```
tune2fs has many other useful options (such as changing max mount count before fsck). Give a look at man page.

---

### Post by DarinB on 2009-06-06
will this reset the amount of mounted times or the max mount count?? i want to reset the amount of mounted times so all three hard drives are at zero and it will start to count again, that way i will know to expect other fscks instead of a surprise

---

### Post by DarinB on 2009-06-06
thanks mirons it worked perfectly. now i am at an a start point an all of my hdd's are at the same mount point thanks.

---

