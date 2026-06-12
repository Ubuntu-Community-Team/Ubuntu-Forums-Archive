---
title: "mpeg and mpeg4 to dvd"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by m3t3ors on 2011-02-09
ive just been looking for an old post i made a while back but cant find it, i wanted to check what software i need to burn mpeg and mpeg4 to dvd to play on standalone dvd players, i know i use brasero to burn the final image to disc but what to use to encode the movies? any help appreciated

---

### Post by Perfect Storm on 2011-02-09
Try with **devede**
It can also make menu, add subtitles, sound tracks etc.

---

### Post by m3t3ors on 2011-02-09
thats the one, thanks i appreciate the help

---

### Post by GrouchyGaijin on 2011-02-09
Try DeVeDe DVD/CD creator to make the .iso file.
I've had better luck burning the .iso to disk using the command line than with anything else.

```


growisofs -speed=2 -dvd-compat -Z /dev/dvdrw=name_of_ISO_File.iso


```

---

### Post by Perfect Storm on 2011-02-10
There's also DVDstyler you could try.

---

