---
title: "[SOLVED] Turn on wireless card"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by Kevbert on 2008-06-30
Hi.  I'm running Ubuntu 7.10 and decided to try Kubuntu Intrepid Alpha1 on a spare partition I had.  Ubuntu 7.10 was working fine prior to the install.
During the start-up of Intrepid, the PC could not find firmware for my Broadcomm BCM4306 wireless card.  I posted on the Development Forum about this.
When I ran up Gutsy no wireless networks could be seen and I could not make any connections - it looks like my wireless card is powered down as 1 get no green lights on the wireless applet.  If I use 
```
iwconfig
```
my card is detected on Eth1 (same as before).  If I use 
```
iwlist scanning
```
no networks are detected.
Is there an easy way to power up my wireless card ?  (preferably via terminal).  
I'm using the same router via my laptop, to write this thread, so I know the other PC should see a network.
Thanks in advance.
Kevin.

---

### Post by Kevbert on 2008-07-01
Solved the problem, but don't know how it occurred.  Went to Restricted Drivers and enabled wireless.  Somehow the firmware had been deleted ????  Once I reinstalled via ethernet and web all is now working again.

---

