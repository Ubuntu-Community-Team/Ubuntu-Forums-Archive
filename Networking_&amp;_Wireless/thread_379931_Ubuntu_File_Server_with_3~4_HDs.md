---
title: "Ubuntu File Server with 3~4 HDs"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by gh0stb0y on 2007-03-09
Hi All, I'm a beginner Ubuntu user (actually, just started 1 day ago) and was trying to setup a file server based off Edgy Eft's Server edition.  There's a guide out there that demonstrates how to setup a LAMP in "45 min".  So far so good but my question is that I've got 2~3 other spare PATA drives that I'd like to add to it, or simply re-install the entire thing and put the drives all together so I can have like a 900GB file server either thru raid or simply just accessing each drive as a separate folder in WinXP/Vista environments.  But I can't seem to find any information as to how to make a sharable folder in the other 2~3 drives after formatting them as ext3 and check to see if the server actually knows that the 2~3 drives are there.  Are there commands similar to that in DOS where you do like a {D:  dir  C:} type of deal?  Sorry, major noob question but I can't seem to find command lines to actually switch to that HD in the prompt(?) and what not.  Thanx in advanced!

edit* I'm aware of other solutions such as FreeNAS, NASLite+, NASLite 2, however I'm a bit interested in some of the Linux worx behind the clicking here and there so this is just the approach I'm trying out.  If nothing worx, then I'll be using FreeNAS, but that doesn't seem all that exciting as it appears so simple that it looks like my DD-WRT menu.  Thanx.

---

### Post by Mr. C. on 2007-03-09
In Unix, don't think separate drives.  All drive that have file systems on them, and are mounted are visible under one namespace, /.  You can see/share/access all of them.

Add the drives anyway you want; you then mount them under / somewhere, and access them in that fashion.

See Week 4 Notes "Filesystems Disks and Partitions"  : [http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

### Post by gh0stb0y on 2007-03-09
Sweet, thanx for the link, I'll definitely spend some time reading it.  Think you've hit the spot as to answer my question.  Btw, you a college prof?  That's kinda cool if you are, hanging around here!

---

### Post by Mr. C. on 2007-03-09
You're welcome.  I hope you find some useful information there.

No, not a prof (I taught for several years for fun), just a guy who's been in this business a long time and enjoys helping people learn about and discover the joy I found many years ago.

MrC

---

