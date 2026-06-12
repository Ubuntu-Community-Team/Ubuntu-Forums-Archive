---
title: "system monitor experiment"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by avacado on 2009-10-19
Pentium 4 - 3GHz
3GB RAM
32 bit Jaunty 9.10
 
I have been trying to load my system with performance tasks.
I used DVDrip, Saurbraten and transfer 7GB of movies to HDD from external.
 
Has anybody noticed that when you open system/administration/system monitor and open the resources tab, network speed and processor fill graphs up to 100% but the RAM only ever seems to use about 8% or 9%.
 
I tried the same experiment with my DELL inspiron 1520 laptop
Intel Centrino dual core t8300 2.4GHz with 4GB ram and 64 bit jaunty
 
The tasks were accomplished much faster, but no more than 8% RAM used.
Huh?
I wonder if I have toggled the wrong switch on system monitor settings.
 
Interesting article on RAM [http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html](http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html)
 
I wonder if I have saturated the pentium IV board with RAM in vain, since it seems it can never all be used....

---

### Post by 3rdalbum on 2009-10-19
The "RAM used" figure in System Monitor refers only to the amount of RAM in active use. Any RAM over and above this will be used as cache, which does definitely speed things up as it avoids the whole "seek the hard disk to this position" bottleneck.

Ubuntu doesn't have a high active RAM requirement, which means it can use loads of cache if you want.

If you'd like to see how much cache is being used, then add the System Monitor applet to your Gnome panel and turn on the "Memory" indicator. The light green/cyan block is the cache, the pine green is the active RAM use.

---

