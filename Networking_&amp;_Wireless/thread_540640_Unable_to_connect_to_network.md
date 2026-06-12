---
title: "Unable to connect to network"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by thekungfuman on 2007-09-01
First let me say that I have tried finding the answer by searching the forum, so I apologize if this has already been handled.

I have a Dell E510 connected to a D-LINK DES-1105 SWITCH (not a router, hence, no firmware). I have a windows XP installation on the SAME hard drive but a different partition (the first partition, followed by Ubuntu, swap, and data) and for some reason I cannot connect to the internet. I don't think my partition configuration is the problem, as I am not able to get online from the LIVE CD either. My windows xp installation does have full internet and networking access. I tried disabling ipv6 in firefox, which didn't work, but even if it did I cannot connect to synaptic or any other services. The network manager says it is connected to the first of two wired services, but the second is grayed out and unusable. Any suggestions or ideas? Please let me know what additional information I can provide that might help diagnose this problem.

---

### Post by CRCarl on 2007-09-02
Are you trying to use DHCP or a static IP?

Please send us the output of ```
ifconfig
```

C

---

### Post by thekungfuman on 2007-09-02
Oddly enough, when I got home from work Ubuntu was connecting just fine. Don't know how, but something sorted itself out. :-)

---

