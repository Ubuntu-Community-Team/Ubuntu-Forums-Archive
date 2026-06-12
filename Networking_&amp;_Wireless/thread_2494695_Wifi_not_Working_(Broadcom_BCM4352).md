---
title: "Wifi not Working (Broadcom BCM4352)"
date: 2024-01-24
forum: Networking &amp; Wireless
---

### Post by atticusjay on 2024-01-24
I have tried many solutions, but for some reason I cannot get ubuntu to pick up the wireless internet card from my laptop. Is there anything I can do?
For some extra information:
```
lspci -nnk | grep 0280 -A3
sudo dpkg -s bcmwl-kernel-source | grep Status
sudo dmesg | grep -e wl -e bcm
```

```

02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0019]
    Kernel modules: bcma, wl
Status: install ok installed
```

---

### Post by tea for one on 2024-01-24
Did you follow the guide?
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by jeremy31 on 2024-01-24
Is Secure Boot enabled?  It has to be disabled for the correct driver to load 
```
mokutil  --sb
```

---

### Post by atticusjay on 2024-01-24
I have followed several guides and none of them have worked until this one. Thank you very much.

---

