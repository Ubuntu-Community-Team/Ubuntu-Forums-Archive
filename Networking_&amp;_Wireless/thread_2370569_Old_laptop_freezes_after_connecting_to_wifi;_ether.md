---
title: "Old laptop freezes after connecting to wifi; ethernet works fine"
date: 2017-09-05
forum: Networking &amp; Wireless
---

### Post by spartina17 on 2017-09-05
Hello,

I'm having trouble getting the wifi to work on my old Toshiba Satellite laptop (ca 2009). Ehernet works fine, but if I disconnect the cable and the computer connects to wifi, the machine always ends up freezing 1-2 min later. Wifi seems to work ok otherwise, as I am able to browse the internet until everything freezes up and I have to reboot the computer.

I'm running Lubuntu. Here is the link to my specs:

[http://paste.ubuntu.com/25469741/](http://paste.ubuntu.com/25469741/)

Also, if this is useful:


```
lspci -v

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device ff01
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f2800000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Toshiba America Info Systems Device ff01
    Flags: bus master, fast devsel, latency 0
    Memory at f2100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f2504800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f4000000-f5ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0000000-c04fffff
    Prefetchable memory behind bridge: 00000000f2000000-00000000f20fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=14, subordinate=14, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f2200000-f22fffff
    Prefetchable memory behind bridge: 00000000c0500000-00000000c06fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: c0700000-c08fffff
    Prefetchable memory behind bridge: 00000000c0900000-00000000c0afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 18a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2504c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=26, subordinate=26, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 29
    I/O ports at 1818 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1810 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at f2504000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: medium devsel, IRQ 10
    Memory at c0b00000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1c00 [size=32]

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at 3000 [size=256]
    Memory at f2010000 (64-bit, prefetchable) [size=4K]
    Memory at f2000000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

14:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8151
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at 4000 [size=256]
    Memory at f2200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl819xE
```


I'm a newbie to Linux. Thanks for your help!

---

### Post by ajgreeny on 2017-09-05
See Wireless-Info in my signature below and follow the info there to run the script and show us the report you get from it.
Someone who is more expert than I with wifi will no doubt be able to help you sort this out.

---

### Post by spartina17 on 2017-09-05
Hi, 

Is this what you're looking for? 

[http://paste.ubuntu.com/25469741/](http://paste.ubuntu.com/25469741/)

Sorry if I'm not understanding, but I did check out the Wireless Info page you are referring to before posting yesterday. I installed the updates and then ran the script I believe you are referring to (please see link above in this post). Let me know if you need anything else!

Thanks again!

---

### Post by spartina17 on 2017-09-22
I resolved the problem by circumventing it: I got a wireless adapter, in this case a [TP-Link Archer T2U AC600 Wireless Dual Band USB Adapter]("http://www.tp-link.com/ca/products/details/cat-11_Archer-T2U.html").

 I had to install the driver which I did by following the instructions at the bottom of this page: [URL="https://github.com/Myria-de/mt7610u_wifi_sta_v3002_dpo_20130916"]Modified usb wifi driver for TP_link TL-WDN5200
[/URL]
I'd like to mention that I got pointed into that direction thanks to Chili 555's answer on this page: [TP-Link AC600 driver on Ubuntu 14.04 LTS x64]("https://askubuntu.com/questions/726569/tp-link-ac600-driver-on-ubuntu-14-04-lts-x64"). Very much appreciated thank you.

I originally posted about the issue on this page and received a few answers which did not solve the problem but were helpful nevertheless:
[SIZE=4][SIZE=2][Old Toshiba laptop freezes after connecting to wifi; ethernet works fine (Ubuntu 14.04.5 LTS)]("https://askubuntu.com/questions/953456/old-toshiba-laptop-freezes-after-connecting-to-wifi-ethernet-works-fine-ubuntu")[/SIZE][/SIZE][B][SIZE=4]
[/SIZE][/B]

---

