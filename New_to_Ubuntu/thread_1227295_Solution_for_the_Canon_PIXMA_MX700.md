---
title: "Solution for the Canon PIXMA MX700"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by A_teen_Geek on 2009-07-30
i was recently looking around for a solution to installing drivers and such for the canon pixma mx700 and i found this post another forum site it has no brainer instructions and is dead simple to follow
[http://forums.linuxmint.com/viewtopic.php?f=51&t=28486&p=165465](http://forums.linuxmint.com/viewtopic.php?f=51&t=28486&p=165465)
i found the links to the .deb files to be broken and i found some others that work fine
[ccnijfilter-common_2.80-1_i386.deb]("http://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu-packages/gutsy/Canon-printing+scan/")
and 
[cnijfilter-mp520series_2.80-1_i386.deb]("http://ftp.akl.lt/baltix-linux/Baltix-Ubuntu-packages/baltix-3.x/Canon-printing+scan/")
 to be future proof if the links break you can search for the deb file on google and add Linux Baltix to the end of it
ex: cnijfilter-mp520series_2.80-1_i386.deb Linux Baltix
i found the sane and the bjnp links to work
as for the canonmx700.ppd.txt file goto this page
[http://ubuntuforums.org/showthread.php?t=571795](http://ubuntuforums.org/showthread.php?t=571795)
scroll down to near the bottom and look at Black Tiger's post
:P
good luck and i hope you arent as frustrated as i was

---

### Post by dannyauble on 2009-10-29
If using 9.10 or later I got these to install by rebuilding the debs work like this...

alien -r cnijfilter-common_2.80-1_i386.deb
alien cnijfilter-common-2.80-2.i386.rpm

and 

alien -r cnijfilter-mp520series-2.80-i.i386.deb
alien cnijfilter-mp520series-2.80-2.i386.rpm

since libcups2 is gone.

then install the debs made after converting from rpms.

Attached is the common deb, the mp520 one was too big to attach ;).

---

### Post by frmdstryr on 2010-06-29
thanks!!

---

### Post by danwoodard on 2011-06-21
Just install CUPS and install the printer, selecting the driver for the CANON PIXMA MP520. It appears to be fully compatible with the CANON Pixma MX700

---

