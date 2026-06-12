---
title: "WLAN suddenly not working after installing IRDA modules"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by leuat on 2007-08-07
Hello  there

I've been running ubuntu on a Thinkpad X41 laptop for a year, with very few problems. The wireless has always worked. This weekend, I installed two new software packages "powertop" (battery lifetime enhancher) and IRDA-modules, to try to get my phone connected. After these packages were installed, the WLAN stopped working. 

iwconfig returns no wlan0 device any more. but a irda0 instead. I tried blacklisting the irda-modules, but nothing happens.

I also notice lsmod doesn't load wlan, ath_pci modules any more  (only ipw2200)

lshw returns wireless network 2915ABG but UNCLAIMED.

Running gutsy. Any ideas? Going nuts here...

---

### Post by newbie1122 on 2007-08-31
hi, this will be off topic but could you please tell how you got the network & wireless to work when you first installed ubuntu on your laptop? i have the same laptop (x41) and i recently installed ubuntu 6.10 on it (im total linux newbie) but i can't connect to network nor internet. 
did you had to install any driver for them to make it work or did it just start working without doing anything?

---

