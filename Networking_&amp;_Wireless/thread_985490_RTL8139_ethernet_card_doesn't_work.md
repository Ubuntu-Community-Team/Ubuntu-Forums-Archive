---
title: "RTL8139 ethernet card doesn't work"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by alexbachmanov on 2008-11-17
Hello, Ubuntu gods/goddesses.
I'm trying to set up a sinfully old computer with Xubuntu, but I appear to be having problems. I bought a Rosewill RC-402 wired ethernet card for it, and it's not working.

Running "lshw" gives:
*-network:0 UNCLAIMED
description: Ethernet controller
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 2
bus info: pci@0000:00:02.0
version: 10
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=64 maxlatency=64 mingnt=32
(Incidentally, this shows up 58 times. I don't know why.)

As I understand it, the drivers for the RTL8139 chip are included with the kernel. Running "lsmod | grep 8139" gives:
8139too     27520  0
8139cp      24704  0
mii         6400   2 8139too,8139cp
(Unfortunately, I have no idea what this means.)

So I'm not entirely sure what I'm doing wrong that's making this not work, but I would tremendously appreciate any light you could shed on this problem.

---

