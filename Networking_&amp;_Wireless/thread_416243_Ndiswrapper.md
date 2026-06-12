---
title: "Ndiswrapper"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by JSpencer87 on 2007-04-20
So after a bunch of trial and error i finally got Ndiswrapper installed using the ubuntu guide and it seemed to install correctly but when i ran the sudo modprobe ndiswrapper command i recieved 

FATAL: Could not open '/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko': No such file or directory

I just need to know what to do next.
Justin

---

### Post by soccrstar on 2007-04-21
ndiswrapper is built in the kernel just not enabled. thats why I think you're getting the error. you need to rebuild the ubuntu kernel with the ndiswrapper enabled. thats my theory

---

