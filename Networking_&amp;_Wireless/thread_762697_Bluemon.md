---
title: "Bluemon"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by ya-manickill on 2008-04-22
Ok,I have spent the past 3 hours trying to find out how to get bluemon to lock my computer when my phone goes out of range of it. I have looked high and low on the internet, and can't seem to find anything.

Does anyone have any ideas?

Thanks.

---

### Post by wipmoneky on 2008-06-09
```
Syntax: bluemon-client <options>
   -u upcmd --upcmd=upcmd
   -d downcmd --downcmd=downcmd
   -b aa:bb:cc:dd:ee:ff --btid=aa:bb:cc:dd:ee:ff
   -v --verbose
   -V --version
   -p --protect
   -h --help

```

 or install blueproximity it is gui and works.

I had to add the paths to the commands ie.
```
gnome-screensaver-command -l
```
to 
```
/usr/bin/gnome-screensaver-command -l
```

if you wanted to run multiple commands I think you could append the line with & like
```
/usr/bin/gnome-screensaver-command -l & /usr/bin/mplayer myvid.avi
```
let me know how it goes.

---

