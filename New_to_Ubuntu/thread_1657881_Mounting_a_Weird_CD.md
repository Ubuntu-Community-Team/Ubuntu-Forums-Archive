---
title: "Mounting a Weird CD"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by crf on 2011-01-01
I'm trying to mount a CD that came with a new Samsung laser printer, so that I can view the user guide.

Ubuntu doesn't auto mount it.
And if I manually mount it (sudo mount -t iso9660 /dev/cdrom ~/testing)
It does mount a filesystem but there's not much in it.

```
~/testing/Linux/noarch/at_opt/share/utils$ ls -a
.  ..  SetIPApplet.html  SetIPApplet.jar
```

... just a directory structure with two files.

But no user guide visible. (I know it's on there ...)

What's going on. Is this CD rom using an odd filesystem which linux cannot read?

Printed below the inner ring of the CD is 
IFPI LC50 (or maybe LC5Q)

(I can get the user guide through windows. But I just want to know why Linux can't wholly read this CD.)

---

### Post by Bucky Ball on 2011-01-01
Does it do the same in Windows? Will it load there?

---

### Post by crf on 2011-01-01
Yes, it works in windows.

There is, though, no directory structure Linux/noarch/at_opt/share/utils/.

While running in windows, there are folders: Application MANUAL Printer Setup.

---

