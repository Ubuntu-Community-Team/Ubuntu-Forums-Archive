---
title: "Ubuntu Installation stalls on Dell Inspiron 700m"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Shahco on 2010-08-23
I am trying to Install Ubuntu 10.04 on an old Dell Inspiron 700m but during the installation, there is a splash of colors on the screen and then it stops and the screen goes blank. Any thoughts? I had installed an earlier version of Ubuntu 2 years ago successfully on this machine with no problems.

---

### Post by kaldor on 2010-08-24
Could you post the specs of the machine? There's not much people can do without knowing a bit more :)

Try burning a new disc (or trying a different distro) to see if the problem persists. Remember to burn the disc at a low (4x is what I use) write speed.

---

### Post by Shahco on 2010-08-27
My system details are:
Intel Pentium M processor 1.60 GHz
589 MHz, 496 MB of RAM
TOSHIBA MK 4026GAX Hard Drive 38155MB with Partition Style = MBR
NEC DVD+- RW ND 6500A CD-ROM Drive
 
I tried downloading it from alternate site and burning at a slow speed but same issue...Trying to convert from Windows to Linux but having problems...Please help

---

### Post by Mercedes300 on 2010-09-17
@Shahco

Post number 12 by twrock has all the info.

[http://ubuntuforums.org/showthread.php?t=1461029&page=2](http://ubuntuforums.org/showthread.php?t=1461029&page=2)

I was able to resurrect an upgraded system with adding "i915.modeset=1" to the end of my kernel line in grub (version 1.x)

Hope this helps.

Manny.

P.S. Good luck with the switch, and welcome to the community! :)

---

