---
title: "Ubuntu 16.04 Dell XPS 13 bluetooth adapter dropping"
date: 2017-09-18
forum: Networking &amp; Wireless
---

### Post by bartvde2 on 2017-09-18
So this happens to me at least once a week, that the bluetooth adapter drops, and my bluetooth mouse won't work anymore. The only way I've been able to work around this is to reboot, change the boot settings to disable bluetooth, reboot again, enable bluetooth and reboot again.

The driver seems to be up to date when I check the version with Synaptic package manager.

TIA for any help.

---

### Post by jeremy31 on 2017-09-18
Post results for ```
lspci -nnk | grep -iA3 net; lsusb
```

---

### Post by bartvde2 on 2017-09-19
3a:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:1535]
	Kernel driver in use: ath10k_pci
	Kernel modules: ath10k_pci
3b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader [10ec:525a] (rev 01)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0c45:670c Microdia 
Bus 001 Device 005: ID 04f3:20d0 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 009: ID 045e:077f Microsoft Corp. 
Bus 001 Device 008: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2017-09-19
Are you using wireless for networking?

---

### Post by bartvde2 on 2017-09-19
yes indeed using Wifi for networking

---

### Post by bartvde2 on 2017-09-19
It mostly seems to happen when the laptop goes to sleep (after coming back from a break), but not every time it goes to sleep the bluetooth adapter drops

---

