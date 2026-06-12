---
title: "Wireless Card Driver - Offline Solution Needed (realtek b822)"
date: 2018-12-27
forum: Networking &amp; Wireless
---

### Post by waterlessland on 2018-12-27
I have recently installed Ubuntu 18.04 on my grandmother's HP Stream 14-ax010wm.  The driver for the wireless card did not install during the OS installation.

I cannot connect the laptop to a router with a hard line and need an offline solution.  I currently have a second laptop to work a solution from.

The information on the wireless card is as follows:

Realtek Semiconductor Co., Ltd. b822
PCI-ID: 14e4:4331
Kernal Modules: r8822be

---

### Post by chili555 on 2018-12-27
> Realtek Semiconductor Co., Ltd. b822
PCI-ID: 14e4:4331
Kernal Modules: r8822beWhat??

14e4:4331 is the pci.id for a Broadcom device. Where did that come from? What does grandmother's computer really contain? Please run and post:```
lspci -nnk | grep 0280 -A3
```In case it is actually the Realtek, also run and post the exact response to these commands:```
sudo modprobe r8822be
dmesg | grep 8822
```

---

### Post by waterlessland on 2018-12-27
Response to command lspci -nnk | grep 0280 -A3


Network Controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
Subsystem: Hewlett-Packard Company Device [103c:831b]
Kernel Modules: r8822be


Response to other two commands:
[ATTACH=CONFIG]282025[/ATTACH]

My apologies for the sideways image, not sure what happened there.

[ATTACH=CONFIG]282026[/ATTACH]

---

### Post by howefield on 2018-12-27
Please copy and paste the terminal output into your post, enclosing between code tags. Make it easier for others to help you.

---

### Post by chili555 on 2018-12-27
‘Required key not available’ means that you must turn off Secure Boot in the BIOS. It is a known bug with no fix quite yet.

After doing so, reboot and the wireless should be working.

---

