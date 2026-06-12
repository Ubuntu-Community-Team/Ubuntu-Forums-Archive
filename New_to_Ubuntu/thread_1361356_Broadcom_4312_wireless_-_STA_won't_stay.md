---
title: "Broadcom 4312 wireless - STA won't stay"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by aa4bb on 2009-12-21
Dell Inspiron 1525 laptop dual boot Vista and Karmic. 

There have been so many posts about this, and I have read until my eyeballs ache and tried many different suggestions over hours and hours. The problem is that STA after getting installed and activated gets kicked out after the next restart.

I am able to get wireless going once in every 10 or so attempts - usually after going to Synaptic, selecting bcmwl-kernel-source and Apply. The wireless light comes on and I'm able to get excellent functioning from the network. However, if I restart or shut down and start back up, the wireless no longer works. When I look at modules, B43 and SSB are back in there, apparently blocking wl from working. Admittedly, I know just enough to be really dangerous, but it seems to be the presence of B43 and SSB that are the culprits. When the wireless is working, all that's in the module listing is wl.

Is there a way to lock the right modules in place, once I have it working?

---

### Post by Cypher1101 on 2009-12-21
[http://www.linuxmint.com/wiki/index.php/Broadcom_bcm43xx](http://www.linuxmint.com/wiki/index.php/Broadcom_bcm43xx)
ignore the part about ndiswrapper, follow every other instruction starting with the line

[FONT=Verdana]sudo gedit /etc/init.d/wirelessfix.sh

My bcm43xx wifi worked perfect after that[/FONT]

---

