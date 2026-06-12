---
title: "Intel(R) PRO/Wireless 3945ABG not working after upgrade"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by frenchsquared on 2008-08-24
product: PRO/Wireless 3945ABG Network Connection

sudo apt-get install linux-backports-modules-hardy-generic
didnt help

gordon@Gateway:~$ sudo rmmod -f iwl3945
[sudo] password for gordon:
ERROR: Removing 'iwl3945': No such file or directory

gordon@Gateway:~$ sudo iwlist wlan0 scan
wlan0 Interface doesn't support scanning.

gordon@Gateway:~$ sudo iwlist wlan0 scan
wlan0 Interface doesn't support scanning.

gordon@Gateway:~$ sudo rmmod -f iwl3945
ERROR: Removing 'iwl3945': No such file or directory

gordon@Gateway:~$ sudo modprobe iwl3945 disable_hw_scan=1
FATAL: Module iwl3945 not found.


any more ideas?

---

