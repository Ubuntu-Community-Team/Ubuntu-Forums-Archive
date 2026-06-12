---
title: "i have a problem with my repository indexes"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2009-05-08
hello everybody,

im having some problems updating my computer recently,
i cant update because i keep gettin an error with my repository indexes.
i get the following error.
> 
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

could somebody please help me with this,
thanks in advanced,
Daniel

---

### Post by huggies15 on 2009-05-08
Hi,
try going to system -> admin ->software sources and untick the installable from cd-rom option
hope that helps it
steve

---

### Post by Pjotrovitz on 2009-05-08
Go to System > Administration > Software Sources

[IMG]http://pjotrovitz.gotdns.org/pics/screen1.png[/IMG]

The checkbox next to the CDROM part at the bottom needs to be unchecked like in the picture.

Good luck!

---

### Post by betterthanjordan79 on 2009-05-08
that was my problem,thanks huggies15!!!

---

### Post by Lucidmez on 2010-04-20
Had the same problem and this worked for me as well.  Thank you.

---

