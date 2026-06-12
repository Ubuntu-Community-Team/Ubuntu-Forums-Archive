---
title: "Unusual networking problem"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by makem2 on 2015-11-21
I have been using xubuntu for months now without networking problems.

Today when I start the machine my networking connection to my router is not in the wifi list of available connections.

I can attempt connections to all those in the list with passwords and can actually connect to BTOpenZone.

After some while my usual network connection reappears in the list and I can connect to it. However, if I reboot, I must go via the BTOpenzone route again to see my own networking connection.

I have rebooted the router and the offending machine. Another computer also running the same version of xubuntu connects and reconnects as does windows 10 on another machine.

---

### Post by makem2 on 2015-11-21
When grub starts I see 3 or 4 lines of errors but to quick to read. Is there any way to find these?

Dmesg is posted at:

[http://paste.ubuntu.com/13409736/](http://paste.ubuntu.com/13409736/)

---

### Post by makem2 on 2015-11-22
Solved:

I had changed the router channel from 11 to 13. This particular machines network card cannot use channel 13.

Changed the channel back to 11 - problem went away.

---

