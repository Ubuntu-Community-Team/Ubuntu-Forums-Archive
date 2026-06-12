---
title: "Wireless Works w/Trial &amp; Not w/8.10 Loaded"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by AustinJM on 2008-12-09
This is on a Dell Inspiron laptop w/Broadcom BCM4312 wireless adapter.

When I use my 8.10 disc as a trial (just run the OS from the disc for a one time session), I am able see, download and activate the proprietary wireless adapter.  With the driver activated, wireless works great.

When I install 8.10, the Hardware Drivers app doesn't list the Broadcom driver as an available driver - so my wireless remains non-functional.

How do I find and install the correct driver?

Thanks for helping a n00b...

---

### Post by Bölvaður on 2008-12-09
Lets begin to speculate.

1. The wireless worked on the cd
2. The wirelss does not work on installed system
3. the system is probably updated with different kernel than is on the cd.


Try find the oldest kernel you can boot from in GRUB. You can tell which one that is by the numbers.


If that doesnt work try looking for ndiswrapper on these forums, they give you opertunity to use windows drivers for the wireless. but you still need to be running on kernel that support that I think

---

### Post by rev0lv3r on 2008-12-09
Lots of times for me, hardware (specifically graphics and wifi) start to work perfectly after 

a) System -> Administration -> Software Sources -> all major repo's are checked
b) Software update is done

Try that before you scrap your install :)

---

