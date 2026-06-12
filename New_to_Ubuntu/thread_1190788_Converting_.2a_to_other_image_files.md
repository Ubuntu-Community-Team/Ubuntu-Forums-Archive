---
title: "Converting .2a to other image files"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by ryniek on 2009-06-18
Hi,

I've been searching for some time in google and here, but i didn't found any answer (maybe i've been searching too short?).
I've got the Minix 3 .2a image file, and i want to convert it to .iso. But i didn't found any application which could do it. Acetoneiso 2 don't support that file type. I've also searched over google to find .2a format specification but nothing found. I know that i must write minix 3 image to usb stick i.e with dd if=/of= command but i want to know, is there something that can convert from/to .2a image file? PowerIso failed, it don't support that file type.  :/

---

### Post by mikechant on 2009-06-18
.2a is *not* an indication of the file type, it is the last part of the minix version number, so trying to convert a '.2a' file will get you nowhere.

If you want a .iso of minix you just download the appropriate .zip or .bz2 compressed file and when you decompress you should get a .iso file. But if you are actually installing via a USB stick, you do not need a .iso file. The image file you have downloaded should be usable with (for example) the Ubuntu supplied 'imagewriter' utility and shouldn't need to have a specific suffix (although if this does turn out to be an issue, renaming the .2a file to .2a.img might help).

The minix download page [http://www.minix3.org/download/](http://www.minix3.org/download/) documents which downloads are suitable for burning CDs from .iso files and which are suitable for writing to USB sticks.

---

### Post by ryniek on 2009-06-18
Ok thanks for answer.  : )

---

