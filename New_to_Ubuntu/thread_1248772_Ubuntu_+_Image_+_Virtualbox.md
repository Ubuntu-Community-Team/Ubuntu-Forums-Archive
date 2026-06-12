---
title: "Ubuntu + Image + Virtualbox"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-24
Ubuntu is the only OS installed on my hdd. Within Ubuntu, I have virtualbox with 2 separate virtual guests. 
 
My setup: 
 
/ = sda1
swap = sda2
home = sda3
 
To the best of my understanding, my virtualbox program is on sda1 but my vdi discs are on sda3.
 
If I use partimage or clonezilla to image sda1 and later use that image to restore, would the restore include my virtualbox program? I would not expect it to restore the vdi discs, since those are on sda3. However, I would expect it to restore the virtualbox program which is on sda1.
 
_My question_:
 
*Am I correct?*

---

### Post by mikewhatever on 2009-08-24
If you image a partition and then restore, everything on that partition will return to the state it was at the time of imaging.

---

