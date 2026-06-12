---
title: "ndiswrapper says driver is correct, but FN+F2 DOES NOTHING"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by JoePits on 2007-05-31
using feisty
removed ndiswrapper and all drivers
installed ndiswrapper and the NETw4x32.INF driver for 4965 wireless
ndiswrapper terminal and gui says its the right driver, but i k now the reason its not working yet is
wireless has to be turned on from the keyboard

FN+F2 does nothing.  the only time it DID do anything in linux was when i had this same setup before but then it stopped working.


what do i have to do...modprobe something?  all the other FN buttons work...

---

### Post by JoePits on 2007-05-31
bump

---

### Post by TheWindsWraith on 2007-05-31
do you have an alternate operating system on the PC? 'Cause if you do you can try activating the card in windows and then rebooting... It worked for me!

EDIT:  You might also try reinstalling the linux-image-2.6.20-16-lowlatency package

---

### Post by JoePits on 2007-05-31
well what do you know i fixed it!

heres how i did it.  disabled networking, sudo modprobe ndiswrapper, hit FN+F2 and wireless light started blinking, reenabled networking  then i saw my network (GIBSON) and was able to connect.

---

