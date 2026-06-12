---
title: "Wireless card displayed as 'Wired'"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by led_belly on 2007-02-19
Hello,

I'm using Ubuntu 6.10 and am trying to get my wireless set up. The problem is my wireless card is listed in the Network Manager as Wired and thus I can't configure it as a wireless connection. Oddly enough, the interface is listed as wlan0, as opposed to eth0. Any ideas on how to remedy this?

Please let me know if you need further information about my hardware.

Thanks!

---

### Post by bvmou on 2007-02-20
Is this a Xircom PCMCIA that has a wired and wireless mode?  I had something similar happen on an old Dell but it worked despite the overlap.  I'm not sure whether it is possible to specify two interfaces and for me it wasnt necessary.  You will sometimes get eth0 and eth1 in these cases.  If it is the Xircom you shouldn't need to use iwconfig, let the NetworkManager defaults do their scanning procedure.

---

### Post by MDFreak76 on 2007-02-27
i dont know if this helps, but before i had to re-install out of desperation (lesson learned: n00bs shouldn't play around as root!) i tried going into synaptic and uninstalling everything related specifically to wireless networking, and i had the same result... if i knew jack diddly about linux i could tell you what to install or reinstall. i am sure this isnt the ideal solution,  but if you are at witt's end, try installing any wireless packages you can find in synaptic...
good luck!

---

