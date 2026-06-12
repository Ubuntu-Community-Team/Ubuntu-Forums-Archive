---
title: "connected thru wireless but iwlist doesnt show my AP  ](*,)"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by Mba7eth on 2007-01-05
Hi guys this is my first post ... and a very newbi to linux .... 
when i am oneline already connected thru wireless fully functioning . but when typing the command : 
#iwlist eth1 scanning     
or 
#iwlist eth1 scan
i got no results  :( 


WHY ](*,) :confused: 

Mba7eth

---

### Post by n00b@linux on 2007-01-05
eth1 is probably your firewire interface (I'm guessing because you didn't post any system specs).
 
Typically:
 
eth0 = ethernet
eth1 = firewire
eth2 = wireless card (mini PCI or mini PCI-Express)
wlan0 = USB wireless adapter
 
Run ```
iwconfig
```and you should see all of your interfaces.

---

