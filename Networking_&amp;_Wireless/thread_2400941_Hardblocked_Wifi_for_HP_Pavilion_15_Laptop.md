---
title: "Hardblocked Wifi for HP Pavilion 15 Laptop"
date: 2018-09-11
forum: Networking &amp; Wireless
---

### Post by reedly on 2018-09-11
Hey y'all,

I just got Ubuntu up and running and I ran right into a problem. My wifi seems to be hardblocked and is resisting my attempts to unblock.

Computer is HP 15-bc251nr.

rfkill lists:

```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

results of `lspci -nnk  | grep -iA2 net`:

```
04:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 61)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5010]
    Kernel driver in use: iwlwifi
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8217]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

My wireless script results: [http://paste.ubuntu.com/p/s4P89xRRK8/](http://paste.ubuntu.com/p/s4P89xRRK8/)

I already reset to defaults on BIOS and have tried both 'sudo modprobe -r hp_wmi' and 'sudo modprobe -r hp_wireless' [FONT=arial]with rfkill unblock all commands.

Anyone have some ideas?[/FONT]

---

### Post by Yellow Pasque on 2018-09-12
Check the obvious first. Have you accidentally pressed the wireless button or airplane mode button? IIRC, they're F11 and/or F12 on HP's.

---

### Post by reedly on 2018-09-12
Yes sir, I'm guessing that that input is what is giving me grief, but no combination of the airplane button with Fn, Ctrl, or plain, whether in Ubuntu or in the BIOS menu has unblocked it.

---

### Post by praseodym on 2018-09-12
Please show
```

lsmod
```

completely

---

