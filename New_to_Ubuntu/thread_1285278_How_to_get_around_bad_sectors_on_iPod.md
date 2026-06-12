---
title: "How to get around bad sectors on iPod"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by djsven on 2009-10-07
My 160GB iPod Classic has bad sectors at the beginning of the drive (only in the first 200MB or so), where iTunes likes to put the firmware files.

Is there a way I can partition / delete this space so that I can force iTunes to put the firmware somewhere else in the available 159.8GB on the drive?

---

### Post by QIII on 2009-10-07
[http://www.macosxhints.com/article.php?story=20060309131841101](http://www.macosxhints.com/article.php?story=20060309131841101)

---

### Post by djsven on 2009-10-07
As it turns out, I had already read that page. Unfortunately the diagnostic mode doesn't seem to have a hard drive scan option on the iPod classic.

I have tried forcing it to read each byte (using dd) hoping that it would automatically mark those sectors as bad, with no luck.

---

### Post by djsven on 2009-10-08
On a related note, if the disk is totally blank, does anyone know what a working iPod will do on start up, i.e. after resetting?

Elsewhere someone mentioned that it asks you to select a language but this seems peculiar if it has no firmware.

---

