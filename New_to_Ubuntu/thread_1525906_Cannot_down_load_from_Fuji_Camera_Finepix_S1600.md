---
title: "Cannot down load from Fuji Camera Finepix S1600"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by ian19jam on 2010-07-07
Can any one kindly advise please as to how I can download my photos from the s00 Fuji Finepix Bridge Camera. The UTP port keeps showing a padlock symbol and refuses to download the SD card. Mine is 4GB. I am a little puzzled as before I upgraded to Ubuntu 10.4 it downloaded normally. 

Some help would be gratefully received.

---

### Post by philinux on 2010-07-07
> **ian19jam said:**
> Can any one kindly advise please as to how I can download my photos from the s00 Fuji Finepix Bridge Camera. The UTP port keeps showing a padlock symbol and refuses to download the SD card. Mine is 4GB. I am a little puzzled as before I upgraded to Ubuntu 10.4 it downloaded normally. 

Some help would be gratefully received.

Maybe try using ```
gksu nautilus
```

It could be a permission problem.

---

### Post by StefQube on 2012-08-05
**Solution** : simple for anyone : :)
in the "Location" bar of a "Nautilus" window -- that is the simple basic "Ubuntu + Gnome" file explorer, just type this :
gphoto2://[usb:001,002]/DCIM
then press "enter"

to get that "Location" bar, in "Nautilus" (if not shown...) press these two keys :
Ctrl L

**Problem** : the above solution solves the following problem :
An automatic Ubuntu update in mai 2012 broke the use I enjoyed of uploading to computer from my camera through USB port + cable :
model : Finepix S1000
maker : Fujifilm  ( Fuji )

---

