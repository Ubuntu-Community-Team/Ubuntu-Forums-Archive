---
title: "IP Connection has hiccaps on Ubuntu 13.10 after update"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by stefanscheiper on 2014-02-02
Hi ... i've updated from 13.04  to 13.10 (64) after that i'm having strange hiccapps from tools like remmina and HPLIP using a HP LaserJet PRO for scanning, printing and faxing, that the communication gets stuck for while and returns sometimes, not all the time. Remmina loses connection through RDP and a windows-machines, reconnect does not always help. With 13.04 the system was running without any of these issues.
Starting a VM with a Windows machine does not show any of these problems.

Configuration:

HP Elitebook 2560p Core I5 with 16GB RAM, Docking Station
LAN connection 1GB, WLAN AGN
HP LaserJet PRO 1415fnw connected through WLAN
Remmina using RDP to Windows XP or Windows 7 hosts (no difference in behavior)


Any thoughts on that ?


Thanks,

-Stefan

---

### Post by stefanscheiper on 2014-02-03
Interesting ... found the problem, it was my router just blocking traffic randomly on my IP-address, changing just the IP-address made the problem disappear .... Sorry Ubuntu, it was not you ;-)

---

