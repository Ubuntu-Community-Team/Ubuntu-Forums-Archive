---
title: "Not able to select my Broadcom drivers on my Ubuntu 16.04 dual boot with windows 10"
date: 2016-07-12
forum: Networking &amp; Wireless
---

### Post by zacmartin on 2016-07-12
I recently installed Ubuntu on my Hp ac-033tx. Even though I am not able to get grub menu I boot into my Ubuntu by ESc > F9 > Ubuntu.
Under additional driver there is listed Broadcom drivers. Wen I select it and click on apply changed after a second it automatically gets unselected.

[COLOR=#111111][FONT=Ubuntu]lspci -nnk | grep 0280 -A213:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]Kernel driver in use: bcma-pci-bridge[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]rfkill list all0: hci0: Bluetooth    Soft blocked: no    Hard blocked: no[/FONT][/COLOR]

---

### Post by chili555 on 2016-07-12
As you are trying to install Additional Drivers, do you have an internet connection? What are the results of these terminal commands?```
sudo dpkg -s bcmwl-kernel-source
```If this says the package is installed correctly, then what does this command report?```
sudo modprobe wl
```

---

### Post by zacmartin on 2016-07-12
Thanks for your reply Sir but I don't know what happened but this time it took 10 mins and got selected to broadcom.

Thank you for your precious time :)

---

