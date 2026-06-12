---
title: "Wired network problem - Realtek driver and Gigabyte GA-990FXA-UD7"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by Resistent on 2013-12-09
Hi all !


I am trying very hard to make my Ethernet work on my  new Motherboard Gigabyte GA-990FXA-UD7, Ubuntu 13.10. I read many forum  entries. But have no solution yet.

Definitely has to be a problem with driver (cable ok, cross straigth type ok - I tested with other PC)

I used kerxy to get the new **linux-headers-3.11.0-15** package and install it,
before I did not have the Realtek r8189 module, but now I have it

```
istvan@Hatvan4:~$ lsmod | grep r8
r8169                  67341  0 
mii                    13934  1 r8169


```

The LSPCI looks like:

```
lspci -v

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 75
    I/O ports at c000 [size=256]
    Memory at fe700000 (64-bit, non-prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
```

I miss there a line which should say Kernel driver:  r8169 .. I think


In the forums I read, we should go back to the Realtek r8101 module , but there is no download any more on the realtek website..


I am already very frustrated..


can somebody give me some hints ?

---

### Post by Resistent on 2013-12-10
No worth to suffer 1 day. I bought a LAN - USB adapter for about 8 USD. I jut plugged in and works works works immediatelly.

---

