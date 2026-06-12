---
title: "Do You See Anything Wrong With This DateStamp?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by mistypotato on 2010-05-08
I can't figure out why this webmin filesystem backup command line doesn't produce a date/time stamp ?

**mysql_`date +'%m.%d.%y_%H.%M'`.tar**

What I get instead is a file with that EXACT name as shown above _**instead**_ of something like this...
[B]
mysql_05.06.2010_13.33.tar[/B]

---

### Post by mistypotato on 2010-05-08
SOLVED
Inside webmin just needed to click on Module Config (Near top of filesystem backup screen) and change this........

**Do strftime  substitution of backup destinations?** 

to YES instead of the default "no"

---

