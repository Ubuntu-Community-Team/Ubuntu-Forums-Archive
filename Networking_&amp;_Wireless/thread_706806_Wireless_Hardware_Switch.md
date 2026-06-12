---
title: "Wireless Hardware Switch"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by tjd_98 on 2008-02-24
Hi, I'm new here and somewhat a beginner to linux. I have a major problem with my wireless (have not been able to make it work in almost six months). I have an Acer Aspire 3620 which I changed the wireless card to an Intel Pro 2915ABG mini PCI card. Now the problem we have narrowed down to the hardware switch. I have run multiple different operating systems (Xubuntu, Fedora 6, Red Hat 5, Solaris 10, Windows XP home, Open SUSE 10.2, Couldn't install Ubuntu) I am now running gOS which is esentially Ubuntu 7.1. The switch was broken and actually came off the board. We replaced it with the identical switch from the blue tooth (not being used) but still cannot get the wireless to turn on. My question is, is there any way to bypass the switch in the programming in any os? The funny part is that with the switch turned off ist still shows as turned on (in windows). Thanks for the help.
Tyler

---

### Post by Whiffle on 2008-02-24
Are you sure this switch actually controls the card?

On mine, its got an rf_kill switch built into the drivers, and I've heard turning the thing on in some cases can be a pain in the butt.  I'll see if I can find anything more specific on this next time I'm using my laptop.

---

### Post by tjd_98 on 2008-02-24
Apparently the switch cust power to the pci slot. I have seen most laptops have a similar switch. I have found a way to bypass almost every major manufacturer except for acer. Most of them have a setting in the bios or in the hardaware something like a driver so if you remove that then the slot always has power. I haven't been able to figure out if the switch is hard or soft (hard being causes an actual circuit break, soft being an auxiliary software device)

---

