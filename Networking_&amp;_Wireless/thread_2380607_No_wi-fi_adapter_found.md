---
title: "No wi-fi adapter found"
date: 2017-12-19
forum: Networking &amp; Wireless
---

### Post by mildelele on 2017-12-19
hi,
I just updated to 17.10 and get the same issue on my Dell Vostro 3446. Spent hours trying to find a fix, getting desperate. Could you pease help?

when I run lspci -nnk | grep -iA3 net I get this:

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0662]
    Kernel driver in use: r8169
    Kernel modules: r8169
08:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)

---

### Post by QIII on 2017-12-19
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2375901](https://ubuntuforums.org/showthread.php?t=2375901)

Please do not hijack the threads of other users.  It becomes confusing for the original poster, you, and anyone attempting to help.

Thanks.

---

### Post by praseodym on 2017-12-19
Please show
```

lspci -nnk
lsusb
pccardctl info
```

---

