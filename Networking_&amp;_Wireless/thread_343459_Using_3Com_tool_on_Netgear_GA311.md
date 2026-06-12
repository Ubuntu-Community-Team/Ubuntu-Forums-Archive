---
title: "Using 3Com tool on Netgear GA311"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by silverado on 2007-01-21
Will the 3com tool mentioned at this thread work on other network cards?  I specifically want it to work on a Netgear GA311 with the Realtek 8169 chip.  

[http://www.ubuntuforums.org/archive/index.php/t-192799.html](http://www.ubuntuforums.org/archive/index.php/t-192799.html)

The tool (3c90xCFG.exe) supposedly changes the chips on some of the cards from "maximum compatibilites" that is to say 10mbps half duplex (speed that all equipement must be compatible with) to "auto-negotiate".  

Any help getting this problem fixed is appreciated, I have been trying to get this to connect to a gigabit switch for three days now, with ethtool telling me it as at half-duplex and 100 mbps (w/ no link found).

Thanks again.  Yours truly, ](*,)

---

### Post by Hanzerik on 2007-01-21
Maybe mii-tool works with your card:

sudo mii-tool -A 100baseTx-FD
or try 
sudo mii-tool -F 100baseTx-FD

[http://www.die.net/doc/linux/man/man8/mii-tool.8.html](http://www.die.net/doc/linux/man/man8/mii-tool.8.html)

---

### Post by silverado on 2007-01-21
I tried mii-tool earlier it said:

SIOCGMIIPHY on 'eth0' failed: Operation not supported.

However, I did get this setup to work.  I swapped out my netgear GS605 gigabit switch with a linksys EG008W 8-port gigabit switch.  Now when I run ethtool, it recognizes it as 1000 mbps and full duplex.  For whatever reason it did not work with the GS605.

---

