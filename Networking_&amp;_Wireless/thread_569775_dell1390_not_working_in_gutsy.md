---
title: "dell1390 not working in gutsy"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by jardo on 2007-10-07
i just made upgrade from feisty to gutsy as finished the upgrade "restricted manager" asked me to installa fwcutter firmware to make working dell card...i followed instructions,but it doesn't work...is that normal?:confused:

---

### Post by kevdog on 2007-10-07
Your missing the user space utilities that goes along with the restricted drivers.  This is normal.  Do you really want to use the bcm43xx drivers anyway??? The max speed of the drivers is 11 Mb/sec, whereas with ndiswrapper it is 54 Mb/sec.  If you choose the ndiswrapper approach, take a look at this thread, this is what I would do:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by jardo on 2007-10-07
yeah,ndiswrapper work very good...but i wish to use native linux driver..i can't get those working... :( i don't know what to do...
about speed 11mb isn't a problem cose my line is 8mb. but i can't get bcm driver working :(

---

