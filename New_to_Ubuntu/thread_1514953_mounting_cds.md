---
title: "mounting cds"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by lolzwut on 2010-06-21
im trying to mount a cd-rom on ubuntu and i just want to make sure i have everything correct before i try to write to it so is /media/cdrom0 where it gets mounted to? That directory is empty by the way.

---

### Post by lolzwut on 2010-06-21
I think i got it now but I'm having trouble getting it to mount

I did this

ls -l /dev/cdrom

and it was linked to sr0 so I did

sudo mount /dev/sr0 /mount/cdrom0

and it said

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type

help me please

---

### Post by lolzwut on 2010-06-21
help plz

---

### Post by lolzwut on 2010-06-21
will someone PLEASE answer me or at least give me some idea

---

### Post by wesleybishop on 2010-06-21
try using acetoneiso

---

### Post by lolzwut on 2010-06-21
> **wesleybishop said:**
> try using acetoneiso


what? can you just tell me how to mount it? It isn't working. It comes up as blank CD-R it doesn't mount

---

### Post by wesleybishop on 2010-06-21
are you trying to mount a iso?

---

### Post by lolzwut on 2010-06-21
I'm trying to mount a cd-rom

---

### Post by wesleybishop on 2010-06-21
check this thread out tell me if it helps [http://ubuntuforums.org/showthread.php?t=458473](http://ubuntuforums.org/showthread.php?t=458473) :p

---

### Post by lolzwut on 2010-06-21
thanks but it didn't work =(

---

### Post by sandyd on 2010-06-21
```

sudo mkdir /media/cdrom0
sudo mount /dev/sr0 -t iso9660 /media/cdrom0

```
sorry, i was watching tv

---

