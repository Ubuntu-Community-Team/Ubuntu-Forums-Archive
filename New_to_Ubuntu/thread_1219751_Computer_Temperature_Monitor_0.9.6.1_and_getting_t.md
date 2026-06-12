---
title: "Computer Temperature Monitor 0.9.6.1 and getting the alarm function to work!"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Koobelakahn on 2009-07-22
running jaunty, and i have this neat little Panel add-on that is supposed to alert me if my CPU is getting too hot.

Unfortunately, i cant get the darn alarm function to work.
Ive tried everything from putting a java program to open up, to something as simple as a gedit document to open up!

can someone please give me a tutorial on this?

any help is greatly appreciated

---

### Post by philinux on 2009-07-22
Looks like there's been no development going on for a while.

[http://computertemp.berlios.de/](http://computertemp.berlios.de/)

---

### Post by Koobelakahn on 2009-07-22
oh wow...
2007...
wow
ok, are there any other applets that are like my current one, but a bit more *ahem* updated?

---

### Post by philinux on 2009-07-22
Yes there is but requires a bit of work. Not too hard.

lm-sensors which is in the repo's. Install via synaptic.

[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

[http://ubuntuforums.org/showthread.php?t=1200182&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=1200182&highlight=lm-sensors)

---

### Post by Mark Phelps on 2009-07-22
You first need to see if the temperatures (temps) can even be monitored.  Install the lm-sensors package as already mentioned.  Then do "sudo sensors-detect" in a terminal.  Reply yes to every question that is asked, and at the end, allow it to make any changes.  Then reboot.

Once back in the desktop, type "sensors" in a terminal.  If you get a bunch of readings, including temps, you're on your way.  If you get few or no readings, there's nothing else you can do.

---

