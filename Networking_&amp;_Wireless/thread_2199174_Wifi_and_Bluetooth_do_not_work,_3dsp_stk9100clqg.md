---
title: "Wifi and Bluetooth do not work, 3dsp stk9100clqg"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by cycloholic on 2014-01-12
Hi, im new on ubuntu, i just installed the latest lubuntu for first time but my wifi+bluetooth combo card wont work. It is a 3dsp stk9100clqg. Is there any way i can fix it?

---

### Post by praseodym on 2014-01-12
Hi,

please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk
lsusb
hciconfig --all 
lsmod
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf 
```
Does LAN work?

---

