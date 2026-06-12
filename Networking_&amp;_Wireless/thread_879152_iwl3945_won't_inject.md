---
title: "iwl3945 won't inject"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by shortridge11 on 2008-08-03
I checked my lsmod and it says i was using the iwl3945 module for my intel pro wireless 3945a/b/g wireless card.  I'm trying to get packet injecting to work, but it won't for some reason.  It's in moniter mode, and nm-applet is killed, but it won't do it.

i did the injection test
[http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=e2252c309028d2da4fd9b130129c044b](http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=e2252c309028d2da4fd9b130129c044b)
and they all failed.  I'm on the correct channel, and there are 10 wireless networks around me all WEP, all failed to inject.  Anybody know what i should do?

---

### Post by shortridge11 on 2008-08-03
=\ bump

---

### Post by shortridge11 on 2008-08-04
i checked out
[http://aircrack-ng.org/doku.php?id=iwl3945](http://aircrack-ng.org/doku.php?id=iwl3945)
for installing and patching the driver, but it's still not really working.  When i put my card in moniter mode, i have to use 
iwconfig (interface) mode monitor
instead of
airmon-ng start (interface)
because the airmon-ng gives me an error.  I know i have the iwl3945 driver because i looked at my output for lsmod, and i saw it in there.  Anyone have any ideas?

---

