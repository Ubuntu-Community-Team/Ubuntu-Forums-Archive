---
title: "eth0 not detected"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by cripperz on 2007-07-28
Hi guys,

is there anyways to detect the lan card back. I previously remove the old lan card and put in a new lan card. now im wondering how to purge the os to detect this new lan card. using ubuntu 6.06 server ... 

pls help

thanks in adv

---

### Post by noob12 on 2007-07-28
Normally you shouldn't really need to do anything if you rebooted.  You may lack drivers for the new card.

Please post the output of

> 
sudo lshw -C network


which will show us the chipset and driver associated (if any) and

> 
lspci -nn


which will list the PCI devices.

---

