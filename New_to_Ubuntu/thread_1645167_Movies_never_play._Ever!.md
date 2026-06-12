---
title: "Movies never play. Ever!"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by adamogardner on 2010-12-14
I started out with Gutsy, then Hardy, now 10.4 (whatever the adjective is I don't know.)  I was hoping by now, I could pop a DVD in and the so-called Movie Player would work.  However the error occurred as I remember, saying the disk could not be read.  It's not a Blueray or anything odd.  It's just a DVD, and I've never enjoyed a movie with Linux, cause it never works.
Am I doing something wrong? Or Not doing something right? Thanks.

---

### Post by staticsafe on 2010-12-14
Take a look at the Medibuntu repository:

[http://medibuntu.org/](http://medibuntu.org/)

You'll need the libdvdcss2 (from the Medibuntu repo) package for encrypted DVDs:

```
sudo apt-get install libdvdcss2
```

You may also want to try VLC.

Also, for other codecs like WMV files, you can read this - [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mastablasta on 2010-12-14
you have to download the restricted extras package (found in repository).

---

### Post by adamogardner on 2010-12-16
I got movies working right away with Staticsafe's recommendation.  I thought I had posted a note of gratitude, but I don't see it.  Thanks for the advice.

---

