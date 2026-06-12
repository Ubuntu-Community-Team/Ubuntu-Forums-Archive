---
title: "trouble with Via-Velocity driver"
date: 2004-12-02
forum: Networking &amp; Wireless
---

### Post by neurator on 2004-12-02
Hello all.  Just installed Ubuntu and my Via Velocity gigabit ethernet card isn't being detected properly.  Its the onboard for the ABIT KV8 Pro MB.  

the default via-velocity.ko file doesn't seem to do the job... I can force the device up, and ping my gateway, but thats it, no other traffic is allowed.  

I downloaded a file, velocityget.tgz, from VIA, which contains a bunch of C files needing compiling.  I tried: 
gcc -c 02 -I/usr/src/linux/include -D_KERNEL -DMODULE velocity_main.c 
but I only get a bunch of errors.  Supposedly its supposed to create a velocityget.ko file that can get worked into the kernel so that the device will work properly.  I installed the version of gcc that comes by default with Ubuntu 4.10.  

Any help in this regard is greatly appreciated.  I'd much rather avoid plopping a different NIC into the system.  

Thank you

---

### Post by neurator on 2004-12-05
Anybody out there have any idea about this?  I haven't found any other conclusive info on the web.  I suppose I might just have to compile the most recent kernel and work with the built-in support that it (supposedly) provides, though it is still beta.

---

### Post by Sindre on 2004-12-07
that nic is supported in 2.6.9

---

### Post by CTD on 2005-02-08
[QUOTE=Sindre]that nic is supported in 2.6.9[/QUOTE]
 Did you ever get this device working?  I'm having the same problem with my KV8 board.

---

