---
title: "Problems with access to a network drive"
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by jacek3 on 2014-01-19
Hi, 

I have a network drive (pseudo-NAS - mynet n900c wd) which, until recently, everything was ok, and currently suffering following problem - Krusader has stopped showing the amount of free space ("No information about the amount of free space on non-local filesystems") and trying to play the media end up downloading everything to / tmp and then running (eg flac file in Amarok starts after download to disk). Previously, it was possible to "stream". Access to the NAS from a network music player or tablet is normal, the files play immediately. What could I mess that I can not see the amount of free space and I can not play the file, but I have to download? 

The disk in fstab (not changed for from the beginning):
```
//mynetn900c/public     /home/kabzior/MyNet     cifs    uid=kabzior     0       0
```

---

