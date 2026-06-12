---
title: "Ubuntu 15.10 No Wireless Chip detected"
date: 2015-12-19
forum: Networking &amp; Wireless
---

### Post by omnicron10 on 2015-12-19
Hello, I am new to Ubuntu but decided to switch as I believe it will help with my Computer Science studies. I just switched my HP Pavilion to Ubuntu 15.10, but it is not detecting the wireless chip and cannot connect to WiFi. Please help.

---

### Post by Hadaka on 2015-12-19
Hi, please go here...
cat   /etc/resolvconf/resolv.conf.d/
then post your wireless-info.txt file
so we may help you find a solution.
thanks.

---

### Post by praseodym on 2015-12-20
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk
lsusb
pccardctl info
lsmod
iwconfig
rfkill list
```

---

### Post by omnicron10 on 2016-01-06
Sorry about the delay, was on holiday

Attachment is the various outputs, thanks for the help!

---

### Post by praseodym on 2016-01-06
```
02:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
	Subsystem: Intel Corporation Dual Band Wireless AC 3165 [8086:4010]
	Kernel driver in use: iwlwifi
```
There it is. Additionally, the module "acer-wmi" is wrongly loaded:
```

sudo rmmod acer_wmi
sudo rfkill unblock all
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

