---
title: "Feisty Fawn -  Belkin 54g F5D7010 won't connect with Network Admin application"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by itsagas2 on 2007-03-27
I installed the new Ubuntu, kernel 2.6.20-12-generic  and the Network Administrator does not work with  my Belkin F5D7010 Wireless Notebook card ( RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01). I have upgraded the kernel to 2.6.20-13generic and I still have the same problem.

I used a beta Ubuntu 7.04 CD to install on my laptop. 

I was using Ubuntu 6.10  prior to this and my Belkin F5D7010 card worked fine and I configured it with the Network Administrator.


The only way I was able to get my Belkin wireless network card to work again was to first issue the terminal command,

sudo ifdown ra0

then after that I issued command

sudo ifup ra0

and my network card came to life.

Is there a :confused:  way I can get my network card to become active on boot up?

---

### Post by itsagas2 on 2007-03-29
I gave up on Feisty Fawn 7.04 Beta and I re-installed Ubuntu 6.06 LTS Dapper Drake.
MUCH Better.

These upgrades are not up to speed with the LTS Draper Drake.

---

### Post by itsagas2 on 2007-07-20
Re installed Festy from scratch, didn't keep my older system files, my home files, and every thing worked fine with my network card:)

---

