---
title: "Intel Wireless-AC 8260 not detected on 16.04"
date: 2017-02-03
forum: Networking &amp; Wireless
---

### Post by Griffnoids on 2017-02-03
Hi,

I've found plenty of articles detailing backports and various fixes for Intel wireless cards on 15.10, however I want to install 16.04 LTS and my laptop has a Intel 8260 wireless card that it can't detect.

Aside from downloading the driver from the Intel site that didn't work, I'm starting to think that the 8260 is just fully incompatible with 16.04?

*lshw -C network* shows an Intel device but doesn't refer to it as wireless and it doesn't have a logical name.

Am I going to have to give up on this and use a USB wireless dongle?

Many thanks.

---

### Post by chili555 on 2017-02-03
> the 8260 is just fully incompatible with 16.04?The default, unmodified 16.04? Yes, correct.> Am I going to have to give up on this and use a USB wireless dongle?
Nope.

Did you try running a live session for 16.10?

---

### Post by jeremy31 on 2017-02-03
It might help if you post results from terminal for ```
lspci -nnk | grep -iA2 net
```
Intel has so many device ID's it isn't possible to tell which one you have from lshw results

---

### Post by spruit on 2017-12-09
I have the same issue and am also on 16.04. Here is the ouput  of lspci that you requested.

spruit@spruit-G752VM:~$ sudo lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by chili555 on 2017-12-09
> **spruit said:**
> I have the same issue and am also on 16.04. Here is the ouput  of lspci that you requested.

spruit@spruit-G752VM:~$ sudo lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169Rather than add to this dead old thread, please start you own new question.

---

