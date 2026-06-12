---
title: "unetbooting not able to make working LiveUSB"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by hesjnet on 2009-05-13
Hi Guys


I have used Unetbootin for making LiveUSBs a couple of times now and it has always worked perfectly. Now when I try it doesn't work. Unetbootin completes without troubles but when I boot up, the bootloader doesn't start. 

I have mtools and 7zip installed. Also I tried both fat16 and fat32. 3 different USB drives from different producers have been used.

Any Ideas?

Thanks

---

### Post by lazyart on 2009-05-13
System>Administration>USB Startup Disk Creator

---

### Post by Peter09 on 2009-05-13
Use gparted to format the drive back to fat32 - delete all the partitions on the drive.

---

### Post by raymondh on 2009-05-13
Lately, I have had more success with ubuntu's imagewriter.

I agree, use gparted to reformat and try again.

Hope this helps.

---

### Post by hesjnet on 2009-05-13
lazyart: Thanks, but this only works on desktop installations. I'm trying to install freedos(I have tried both the Freedos 1.0 version from unetbootin and 2 different iso's from their website)

Peter09: Thanks but I already did that several times.:-(

raymondhenson: imagewriter apparently only works with .img files, not .iso

---

