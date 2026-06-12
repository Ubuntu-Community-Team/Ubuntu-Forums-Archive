---
title: "Newer e1000e driver in 14.04?"
date: 2014-11-20
forum: Networking &amp; Wireless
---

### Post by Explodinglemur on 2014-11-20
I installed 14.04.1 server 64bit on a system with an Intel I218V Ethernet interface. However, the version of the e1000e driver included with the 14.04 kernel (2.3.2 from March 2013) doesn't support this adapter (not surprising, as it didn't exist then). I ended up downloading the 3.1.0.2 source and compiling it, now the network interface works fine. BUT... With this being the case, I'm going to have to remember to compile this driver manually every time a new kernel package is installed. Since this is a headless system, I can easily see myself forgetting and locking myself out of the machine by way of breaking the network interface. What would the best solution for this be? I want to stay on top of security updates and patches with new kernel packages, so just pinning the current kernel is non-ideal.

---

