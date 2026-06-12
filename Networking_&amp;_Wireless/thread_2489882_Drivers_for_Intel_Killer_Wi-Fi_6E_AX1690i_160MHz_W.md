---
title: "Drivers for Intel Killer Wi-Fi 6E AX1690i 160MHz Wireless Network Adapter"
date: 2023-08-13
forum: Networking &amp; Wireless
---

### Post by yooakim on 2023-08-13
I have a new Intel NUC computer (NUC13SBBi9) and it came with a Intel Killer Wi-Fi 6E AX1690i 160MHz Wireless Network Adapter.

I have tried to get this to work with Ubuntu 22.04.3 LTS and also 23.04 but have failed.

Anyone here who could help?

---

### Post by readableauthor on 2023-08-13
Try this:
```

sudo apt-get install backport-iwlwifi-dkms

```
Then reboot

---

### Post by jeremy31 on 2023-08-13
Can you post results from terminal for ```
lspci -nnk | grep -iA3 net
```

Moved to Networking & Wireless

---

### Post by yooakim on 2023-08-14
The output of lspci -nnk is:

```
00:14.3 Network controller [0280]: Intel Corporation Device [8086:7af0] (rev 11)
    Subsystem: Rivet Networks Device [1a56:1692]
    Kernel modules: iwlwifi
00:15.0 Serial bus controller [0c80]: Intel Corporation Device [8086:7acc] (rev 11)
    Subsystem: Intel Corporation Device [8086:3033]
--
07:00.0 Ethernet controller [0200]: Aquantia Corp. Device [1d6a:14c0] (rev 03)
    Subsystem: Intel Corporation Device [8086:3033]
    Kernel driver in use: atlantic
    Kernel modules: atlantic
08:00.0 Ethernet controller [0200]: Intel Corporation Device [8086:125c] (rev 04)
    Subsystem: Intel Corporation Device [8086:0000]
    Kernel driver in use: igc
    Kernel modules: igc

```

---

### Post by jeremy31 on 2023-08-14
Any results for ```
sudo dmesg | grep iwl
```

---

### Post by yooakim on 2023-09-07
The output of `[FONT=courier new]sudo dmesg | grep iwl[/FONT]` is

[FONT=courier new]iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
iwlwifi: No config found for PCI dev 7af0/1692, rev=0x430, rfid=0x3010d00
iwlwifi: probe of 0000:00:14.3 failed with error -22
[/FONT]
 Not sure what I can / should do?

---

### Post by readableauthor on 2023-09-07
[https://github.com/torvalds/linux/commit/4e9f0ec38852c18faa9689322e758575af33e5d4](https://github.com/torvalds/linux/commit/4e9f0ec38852c18faa9689322e758575af33e5d4)
Your device seems to be supported starting from Linux 6.4. You can try updating your kernel. backport-iwlwifi-dkms should be removed in that case.

UPD: the same fix seems to be present in OEM Ubuntu kernel. You could try it this way:
```

sudo apt install linux-oem-22.04c

```

---

### Post by yooakim on 2023-09-08
Thanks, I'll try. I'm not sure how I can get this done then the target machine (with the issue) does not have Internet connection.

What do I need to download (on another machine) to get this?

---

### Post by readableauthor on 2023-09-08
Can you use your phone's USB tethering?

---

### Post by yooakim on 2023-09-08
Ah, good idea - I'll see if that works :-)

---

