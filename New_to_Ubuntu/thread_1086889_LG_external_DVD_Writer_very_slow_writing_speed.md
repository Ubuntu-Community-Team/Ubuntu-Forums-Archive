---
title: "LG external DVD Writer very slow writing speed"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Geo_V on 2009-03-04
Hi everyone,

i have a Toshiba laptop to which i have connected an external lg dvd writer with writing capabilities at 20x(DVD). However, i could never achieve writing speed above 3x or 2x...This DVD drive can write at 20x, tested on Widows many times.

I've installed Brasero, Gnome CD Master and K3b.

It would be much appreciated if someone knew the solution, cause its very annoying having to switch to windows every time i want to burn a DVD....

Thanks in advance..

---

### Post by albandy on 2009-03-04
It depends on your internal usb hub version.

for usb 1.1 the speed it's about 15 Mbit/s (about 1.86 MB/s)
for usb 2.0 the speed it's about 480 Mbit/s (about 60 MB/s)

---

### Post by Geo_V on 2009-03-04
Both then DVD and the laptop have usb 2.0 support. As i said previoysly, the dvd achieves speeds of 20x in Windows, so i has to be some other matter i suppose..Thanks anyway for the answer...

---

### Post by albandy on 2009-03-05
and reading? test it reading a cd

---

### Post by mikechant on 2009-03-05
In the DVD writer applications, did you set the writing speed manually or let it default? Maybe the defaults are too low.

---

### Post by Geo_V on 2009-03-05
Well, i didn't chech the reading speed albandy but the reading does not seem to have any problems.

Also, as mikechant mentioned, i haven't set any writing speed manually, so i guess is must have the default values.

However, i need some directions about how to check both the reading speed and to set the writing speed manually, since im a bit new to linux..

---

### Post by Geo_V on 2009-03-05
My mistake, i manually set the writing speed at 20x in the DVD writer applications...i didn't understand correct firsty. Still though, the writing speed kept under 4x.

---

### Post by LowSky on 2009-03-05
is it 64bit Ubuntu?
its a known issue since 8.04.1 kenel update.
I too am suffering from it, it kinda sucks, there isn't really a workaround

---

### Post by Geo_V on 2009-03-05
I have installed Ubuntu Studio or more specific

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

---

### Post by Geo_V on 2009-03-05
Is it possible that there is no solution to this? I can't believe they did such a big mistake...

---

### Post by Geo_V on 2009-03-06
Any help would be much appreciated....

---

### Post by albandy on 2009-03-06
try with the previous kernel version

---

