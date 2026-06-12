---
title: "Hcitool: Blutooth Logging"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by EddieR91 on 2008-07-15
Hi All.

I'm kinda new to linux, (however not a complete novice). what i'm trying to do is to program hcitool to scan for devices, then output the results to a file...and loop. 

I've search the internet for help, but to no avail. Anybody have any ideas?

---

### Post by Kevbert on 2008-07-15
You could use
```
hcitool > test.txt
```
Add the extras to the end of hcitool.
If you need to loop it you'll need to create a bash script or maybe something in python (I'm new to this also).

---

