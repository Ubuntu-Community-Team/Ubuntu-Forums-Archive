---
title: "No internet connection (cable unplugged)"
date: 2015-06-14
forum: Networking &amp; Wireless
---

### Post by Jan.zmazek on 2015-06-14
Hello, yesterday I decided to install fresh version of Ubuntu 14.04 (I was using Windows 7 before). Everything was fine until i tried to connect to the internet. Ethernet cable is plugged in (worked in windows 7) and orange led is blinking. I read on forums that the problem was my ethernet controller driver; I'm using 

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at c000 [size=256]
    Memory at e8010000 (64-bit, prefetchable) [size=4K]
    Memory at e8000000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at e7000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8168

Kernel driver at fresh install was r8169. I have already done everything i found on forums about this topic. I downloaded r8168 driver from realtek webpage, installed it, blacklisted r8169 driver etc. However, in the network settings, there is still "cable unplugged" message. Please help.

---

