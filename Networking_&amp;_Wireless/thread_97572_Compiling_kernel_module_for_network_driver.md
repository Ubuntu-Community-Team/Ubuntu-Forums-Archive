---
title: "Compiling kernel module for network driver?"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by dominik_l on 2005-12-01
Hi,

my problem is, that ubuntu does not recognize my built-in lan device (Sis190 on Asrock 939S56-M mainboard). But SIS offers a linux driver for it.
But because I have no internet connection in ubuntu, I cannot make a "apt-get install build-essentials" for compiling a kernel module. Can please anyone tell me exactly what packages I need and where to get them? I don't want to spend the night watching the boot screen when switching from ubuntu to windows over and over again...

Thanks a lot!

Best regards,
Dominik

---

### Post by az on 2005-12-01
build-essential is on the install cd.  You can and should install it.

The kernel was not built with the compiler version that you have, though.  You need to install gcc-3.4 (there are three packages look on packages.ubuntu.com) that is all.

Once you get your device running, file a bug report, please.

bugzilla.ubuntu.com  

the package to file the bug for is linux-image.

---

### Post by dominik_l on 2005-12-01
Ah, build-essiential is on the install cd... 
Ok, thanks!

Dominik

---

