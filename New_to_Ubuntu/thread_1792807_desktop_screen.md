---
title: "desktop screen"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by gridd on 2011-06-28
hi  I am using an acer laptop having just loaded and run Xubuntu 11.04 

strangely along with the usual icons Every partition and other oss are also icon d. But not mounted on my desktop, I cant delete or get rid of them,options greyed out or not there. md5 has checked out ok.  how can I remove them.

---

### Post by Wobblybob on 2011-06-28
Have you tried, [Settings], [Settings Manager], [Desktop], icons tab and removed the default icons ?

---

### Post by Toz on 2011-06-28
You can also create a udev rule to hide the partitions you don't want seen by Ubuntu ala:
> $ cat /etc/udev/rules.d/10-local.rules 
KERNEL=="sda1", ENV{UDISKS_PRESENTATION_HIDE}="1"

You can still access the paritions, if required.

---

