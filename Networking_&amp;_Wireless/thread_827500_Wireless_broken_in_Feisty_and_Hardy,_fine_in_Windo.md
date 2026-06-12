---
title: "Wireless broken in Feisty and Hardy, fine in Windows"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by dandelions on 2008-06-12
I have two computers, one dual-booting Feisty and XP, and the other dual-booting Hardy and Vista. They both connect to a router using wireless access, and this was working in all four OSes up until a couple of days ago, when both Hardy and Feisty's wireless connections broke. Vista and XP are both still fine, so it's not an issue with the wireless cards. iwconfig in both shows that the wireless is there and properly detected, though they don't have the essid and so on that they ought to have in a proper connection. sudo /etc/init.d/networking restart and wlan1/eth1 up don't help.

Any ideas?

---

### Post by superprash2003 on 2008-06-12
try enabling an restricted drivers under System->administration->Restricted drivers (or hardware drivers)

---

### Post by dandelions on 2008-06-13
They're enabled, where necessary - one's using the broadcom43xx drivers and the other ndiswrapper with realtek drivers. Since they both worked and I've not changed the drivers since, I think it's not a driver problem.

---

