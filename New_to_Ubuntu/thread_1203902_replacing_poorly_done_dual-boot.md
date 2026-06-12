---
title: "replacing poorly done dual-boot"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by gbttun on 2009-07-04
A couple weeks past, I installed Dapper Drake from a CD, but did it poorly. Despite doing a dual-boot, I am unable to access Windows Vista using the GRUB (perhaps I am doing it improperly). The main issue with Drake is the incompatibility of the wireless card--Broadcom 4311.
Jaunty Jackolope has arrived from Canonical now, and I wish to replace Drake, but maintain the dual boot with Vista. On the install screen, however, I cannot completely erase the Drake partition. Is it possible to do so?
[SIZE=1][/SIZE]


Thank you for your help in advance.

---

### Post by earthpigg on 2009-07-04
boot from the live cd and select 'try without making any changes'

once the ubuntu desktop boots from the live cd, go to applications -> accessories -> terminal, and run

gparted


graphical user interface to play around with partitions. reformat your dapper drake partition as something else, then hit the 'install ubuntu' icon on the desktop and see if that clears the issue up for you.

---

