---
title: "Intel Wireless-N 7260 Ubuntu 14.04 compatibility?"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by robert-grimm7 on 2014-12-03
I have searched all over trying to install a working wireless driver for this card on my ubuntu installation. i have a Lenovo T440s with the Intel Wireless-N 7260 card installed - works fine on Windows 8.1.

Thanks in advance

---

### Post by carl4926 on 2014-12-03
Boot ubuntu live
and see
If it's going to work, it should do so in the live system

---

### Post by ajgreeny on 2014-12-03
I have just installed Xubuntu 14.04.1 on a new laptop with INTEL® N-7260 (300Mbps, 802.11BGN) wireless, and that is working fine, so it is not just the card causing the problem.

---

### Post by jeremy31 on 2014-12-03
If you have a wired connection available, run the software update program or in terminal ```
sudo apt-get update && sudo apt-get upgrade
```
The answer might be in Ubuntu kernel 3.13.0-40 if ```
lspci -nnk | grep -iA2 net
``` shows this as your wifi```
[COLOR=#2E8B57][FONT=Monaco]02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev cb)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        Subsystem: Intel Corporation Device [8086:4c70][/FONT][/COLOR]
```

---

### Post by chili555 on 2014-12-03
> **robert-grimm7 said:**
> I have searched all over trying to install a working wireless driver for this card on my ubuntu installation. i have a Lenovo T440s with the Intel Wireless-N 7260 card installed - works fine on Windows 8.1.

Thanks in advanceCheck to see that the switch or key combination is set to enable wireless:```
rfkill list all
```The driver iwlwifi is included in recent Ubuntu versions. See if it loaded:```
lsmod | grep iwl
```If not, load it:```
sudo modprobe iwlwifi
```Finally, check for errors, warnings, etc. in the log:```
dmesg | grep iwl
```

---

