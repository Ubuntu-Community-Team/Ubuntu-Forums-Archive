---
title: "Wireless problems with wireless after suspend"
date: 2015-10-11
forum: Networking &amp; Wireless
---

### Post by mistcloud-misty on 2015-10-11
I am running 14.04 on Asus x555L. I have two problems with my wireless.

After waking up from suspend, about 75% of the time, my wireless takes a long time to connect. It repeatedly disconnects while trying to connect again to the wireless which is available. Within a minute it usually connects and works fine until the next suspend if I'm on the home network. After reboot, the Internet always works fine from the home network. 

A different problem occurs at the campus network, which is a wireless network that redirects you the first time you use it so you can login to the campus security  and gain access. It constantly disconnects and reconnects, and I cannot get it to simply stay connected. 

This is the Ethernet and Network controllers: ```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e084]
    Kernel driver in use: mt7630e
```

I installed the driver and followed the instructions on [this](http://community.linuxmint.com/tutorial/view/1796) page to initially get the wireless working. 

I am attaching part of my PM logs (too big to fit the whole file in an attachment). 

Any ideas?

---

