---
title: "Ubuntu 8.10 - cannot connect to wired network when wireless card installed"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by kevinatkins on 2008-11-09
Hi,

I've just installed Ubuntu 8.10 on an old IBM ThinkPad T30. I'm experiencing a strange problem. If I boot the system with the mini-pci wireless network card installed on the system, I cannot seem to connect to the wired network with Network Manager - it attempts to connect, the two blobs go green, then after a short while of trying to connect, it drops back to no network connection... If I remove the wireless card, everything is OK. 

This behaviour is new - with 8.04 it worked fine!

Has anybody else seen this?

TIA.

Kevin.

---

### Post by kevinatkins on 2008-11-09
Hi folks,

well I seem to have got it working.. I don't know what happened, but reseating the wireless card appears to have cured the problem.

Cheers,

Kevin.

---

### Post by bikerbrock on 2009-02-14
I am having the same exact problem.  I recently installed a new wireless mini-pci adapter (linux drivers available) and the wired connection doesn't work any more.  I have dual boot and it works in windows though....  I also tried re-installing ubuntu 8.10 with no luck.  It seems that the dhclient tries a broadcast but gets no replies.  I will try reseating the wireless card even though it seems like a long shot...

---

### Post by superprash2003 on 2009-02-14
post ifconfig output from the terminal.. you may have ips of the same gateway on both cards..

---

