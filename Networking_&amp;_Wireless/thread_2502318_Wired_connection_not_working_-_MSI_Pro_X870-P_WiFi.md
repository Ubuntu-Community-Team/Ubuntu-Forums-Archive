---
title: "Wired connection not working - MSI Pro X870-P WiFi - Ubuntu 24.10"
date: 2024-11-09
forum: Networking &amp; Wireless
---

### Post by joaocrespo on 2024-11-09
Hello world.

Just did an hardware upgrade and got a motherboard ATX MSI Pro X870-P WiFi, the WIFI works but the Wired connection does not  (in Windows works without an issue).

Did some googling around (but failed to solve the issue), and here is some output i think may help identify the problem:

```
lspci -knn | grep Eth -A3
```

```
0d:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:8126] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7e47]
    Kernel modules: r8169
0e:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1064 Serial ATA Controller [1b21:1064] (rev 02)

```

```
sudo dmesg | grep -i r8169
```

```
[    0.606554] r8169 0000:0d:00.0: enabling device (0000 -> 0003)
[    0.606602] r8169 0000:0d:00.0: error -ENODEV: unknown chip XID 64a, contact r8169 maintainers (see MAINTAINERS file)

```

---

