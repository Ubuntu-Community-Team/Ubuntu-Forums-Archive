---
title: "Wireless Driver Installation and detection Issues"
date: 2015-12-10
forum: Networking &amp; Wireless
---

### Post by Uday_Vyas on 2015-12-10
Just installed Ubuntu on my laptop (Lenovo y700 14ISK).  However, I  am unable to get my wifi working. Going through multiple forum posts, I  figured out that I need to find the wifi chipset Type using commands  like lspci -v. And, install the controller drivers accordingly. However,  I am confused with response received for lspci -v as it seems to be  returning both network as well as ethernet controller. But, There is no  identifier that clearly states wireless chipset. Any help with figuring  out right chipset and getting wifi driver installed is highly  appreciated.


  The following is response from lspci -v, rfkill list & lspci -nn | grep -e 0200 -e 0280 commands:      

14ISK:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Device 1910 (rev 07)
    Subsystem: Lenovo Device 3806
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Device 1901 (rev 07) (prog-if 00
[Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: a1000000-a1ffffff
    Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev
06) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3807
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Memory at a0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915_bpo

00:14.0 USB controller: Intel Corporation Device a12f (rev 31)
(prog-if 30 [XHCI])
    Subsystem: Lenovo Device 3806
    Flags: bus master, medium devsel, latency 0, IRQ 123
    Memory at a2300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:14.2 Signal processing controller: Intel Corporation Device a131 (rev 31)
    Subsystem: Lenovo Device 3806
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at a232a000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

00:16.0 Communication controller: Intel Corporation Device a13a (rev 31)
    Subsystem: Lenovo Device 3806
    Flags: fast devsel, IRQ 255
    Memory at a232b000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>

00:17.0 SATA controller: Intel Corporation Device a103 (rev 31)
(prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 3806
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 124
    Memory at a2328000 (32-bit, non-prefetchable) [size=8K]
    Memory at a232e000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5080 [size=8]
    I/O ports at 5088 [size=4]
    I/O ports at 5060 [size=32]
    Memory at a232c000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1c.0 PCI bridge: Intel Corporation Device a115 (rev f1) (prog-if 00
[Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: a2200000-a22fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 PCI bridge: Intel Corporation Device a11a (rev f1) (prog-if 00
[Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: a2100000-a21fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.3 PCI bridge: Intel Corporation Device a11b (rev f1) (prog-if 00
[Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: a2000000-a20fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1f.0 ISA bridge: Intel Corporation Device a14e (rev 31)
    Subsystem: Lenovo Device 3806
    Flags: bus master, medium devsel, latency 0

00:1f.2 Memory controller: Intel Corporation Device a121 (rev 31)
    Subsystem: Lenovo Device 3806
    Flags: bus master, fast devsel, latency 0
    Memory at a2324000 (32-bit, non-prefetchable) [size=16K]

00:1f.3 Audio device: Intel Corporation Device a170 (rev 31)
    Subsystem: Lenovo Device 3806
    Flags: bus master, fast devsel, latency 32, IRQ 127
    Memory at a2320000 (64-bit, non-prefetchable) [size=16K]
    Memory at a2310000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1f.4 SMBus: Intel Corporation Device a123 (rev 31)
    Subsystem: Lenovo Device 3806
    Flags: medium devsel, IRQ 255
    Memory at a232d000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]

01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI]
Venus XTX [Radeon HD 8890M] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: radeon

07:00.0 Network controller: Intel Corporation Device 3166 (rev 79)
    Subsystem: Intel Corporation Device 4210
    Flags: fast devsel, IRQ 255
    Memory at a2200000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>

08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd.
Device 524a (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 524a
    Flags: fast devsel, IRQ 255
    Memory at a2100000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.
RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Lenovo Device 3836
    Flags: bus master, fast devsel, latency 0, IRQ 125
    I/O ports at 3000 [size=256]
    Memory at a2004000 (64-bit, non-prefetchable) [size=4K]
    Memory at a2000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169


14ISK:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


14ISK:~$ lspci -nn | grep -e 0200 -e 0280
07:00.0 Network controller [0280]: Intel Corporation Device [8086:3166] (rev 79)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)

Thanks in Advance!!

---

### Post by weatherman2 on 2015-12-10
Try the Networking and Wireless forum.  Read the "sticky" post at the top about running the wireless script and posting the results in a new thread (or wait for this thread to get moved).

---

### Post by jeremy31 on 2015-12-10
What kernel are you using ```
uname -a
```

---

### Post by Yellow Pasque on 2015-12-10
```
07:00.0 Network controller [0280]: Intel Corporation Device [8086:3166] (rev 79)
```

Looks like an Intel 3165: [https://wikidevi.com/wiki/Intel](https://wikidevi.com/wiki/Intel)

Perhaps this will help: [http://askubuntu.com/questions/666623/nuc-5cpyh-intel-3165-ubuntu-15-04-or-14-04-heres-how](http://askubuntu.com/questions/666623/nuc-5cpyh-intel-3165-ubuntu-15-04-or-14-04-heres-how)

---

### Post by bapoumba on 2015-12-12
*Thread moved to **Networking & Wireless**.*

---

