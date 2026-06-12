---
title: "Network Card Firmware"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by Jordan_Henley on 2014-05-28
My Problem: No firmware for my wireless card.

OS: Elementary OS - Luna (Based off of Ubuntu 12.04)

Wireless Card: Realtek RTL8101 / RTL8101E PCI Express Fast Ethernet Controller

I cant figure out how to get the firmware for this, all 'fixes' I tried either broke the system, or froze it.

---

### Post by praseodym on 2014-05-29
Hi,

that looks like the LAN card ;)

Please check the terminal outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
pccardctl info
lsmod
iwconfig
rfkill list
```

---

