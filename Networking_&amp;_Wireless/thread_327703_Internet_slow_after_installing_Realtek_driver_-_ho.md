---
title: "Internet slow after installing Realtek driver - how do I remove it?"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by Crakie on 2006-12-29
In trying to get WakeOnLan supported, I installed the r1000_v1.05 driver for the Realtek Gigabit LAN chipset on my AB9 Pro motherboard. Unfortunately, WOL is still not supported and, even worse, internet got annoyingly slow. 

How do I remove this kernel module (which I think it is) and restore the connection settings I was using before? I never fooled around with the connection settings that came with my Kubuntu Edgy install - it worked fine right from the liveCD and the subsequent install.

Of course, any other solution that speeds up my connection is fine too, but removing the module seems the easiest way to go :)

---

### Post by teaker1s on 2006-12-29
with module-assistant

add cd with synaptic or  apt-get  then  update  and install

---

### Post by Crakie on 2006-12-29
Thanks, but that didn't get my anywhere. I cannot find the r1000 (=the name of the driver) module in the list... so it's not a module?

I found a way to reconfigure my ethernet adapter using etherconf... this seems to work (no errors), but doesn't solve the problem. So the problem is rooted 'deeper' into the system. Basically I want to restore all relevant settings to the way kubuntu installed them.

---

