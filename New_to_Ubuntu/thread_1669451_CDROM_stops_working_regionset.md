---
title: "CDROM stops working regionset"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by omkarwagh on 2011-01-17
Hey
I have a region 2 drive.
I used to be able to mount region 1 drives (but not play them) with a dialog opening asking me if I want to change my region. I never really changed the region though. 
However, suddenly no cd/dvd from region 1 can now be mounted on my drive (let along playing them). 
This seems to be a hardware issue since it's there even in windows. 

And regionset doesn't work without a cd being in the drive first. 

Any help? 
Thanks.

---

### Post by davidmohammed on 2011-01-17
some CDROM/dvd drives only allow you to change the region a certain number of times before preventing you from changing the region again.  

You may have one of those drives...

---

### Post by gabriel8a2002 on 2011-01-17
hey omar, if you use libdvdcss2 for your drive, and you never have to worry about "region" sets.

also if you are on windows, anydvd will do that too, jst that libdvdcss2 is free :p. Im playing DVDs from Mexico (Region 4) on my USA computer (Region 1).

---

### Post by robert shearer on 2011-01-17
What application are you using to play these ??

---

### Post by deanjm1963 on 2011-01-17
> **gabriel8a2002 said:**
> hey omar, if you use libdvdcss2 for your drive, and you never have to worry about "region" sets.

also if you are on windows, anydvd will do that too, jst that libdvdcss2 is free :p. Im playing DVDs from Mexico (Region 4) on my USA computer (Region 1).

libdvdcss2 is just for decrypting the dvd to play. If you are using VLC to play dvds it bypasses the region encoding completely.


@ omkarwagh - I suggest you put in a region 2 disk and use regionset to set it back to region 2 and use VLC with libdvdcss2 (which is available via the Medibuntu repo) and play dvds that way.

Hope this helps.

---

