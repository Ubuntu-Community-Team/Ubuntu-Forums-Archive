---
title: "ndiswrapper binary"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by measekite on 2007-09-20
IS there any palce to download a binary (compiled) or (deb) version of ndis wrapper so I will not have to bother compiling it?  If so please post the url.

Once it is installed do you just pop in the factor Linkysis Wireless Card CD and executive it from there?

---

### Post by ddrichardson on 2007-09-21
ndisgtk is in the repos and lets you graphically add the driver without compiling.

---

### Post by noob12 on 2007-09-21
Well ndiswrapper 1.38 ships with Ubuntu 7.04.  You just need to install the utils package (ndiswrapper-utils-1.9), but the driver is there.  Unfortunately, it's way behind the current driver version 1.48 that you can get if you compile from sources.

A lot of people have found that to get reliable wireless with ndiswrapper they had to use a more recent driver version than what's in Feisty.

---

### Post by kevdog on 2007-09-21
ndiswrapper is compiled against the kernel, so I think if you ever changed kernel versions -- like the transistion from edgy->feisty and feisty->gusty, that there could be a problem (theoretically).  It really doesnt take much work to compile from source, and you get the latest version.   One of the major problems IMO is that with debian based OS versions, a lot of the software in the repositories is very old.  If you dont like working with older software, then I guess this wouldnt be a problem however.

---

