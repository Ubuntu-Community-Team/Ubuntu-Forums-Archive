---
title: "Intel 3945ABG, Lubuntu 14.04 - Problem with WiFi Connection"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by kostas_katsikantai on 2014-11-25
Hi

I have installed Lubuntu 14.04 on my laptop.
It's HP Compaq 6710b.

In Lubuntu I'm able to access the internet via wired connection 
but I can't access the internet using WiFi.

Please help.

* I saw a familiar Thread about this which I tried but didn't worked.
   I post the result of the command "lspci -nn" and I hope it will help.

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
            Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
            Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
            Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
            Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: ahci
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
            Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
            Kernel driver in use: yenta_cardbus
02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02)
            Subsystem: Hewlett-Packard Company Device [103c:30c0]
            Kernel driver in use: firewire_ohci
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
            Subsystem: Hewlett-Packard Company PRO/Wireless 3945ABG [Golan] Network Connection [103c:135c]
            Kernel driver in use: iwl3945
18:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
            Subsystem: Hewlett-Packard Company 6710b [103c:30c0]
            Kernel driver in use: tg3

```

---

### Post by chili555 on 2014-11-25
Let's gather just a bit more information:```
rfkill list all
dmesg | grep iwl

```Thanks.

---

### Post by kostas_katsikantai on 2014-11-25
While I was waiting for someone to response I did Software Update with the wired connection and after the restart 
the WiFi connection is working perfectly :)

Thanks anyway for the help :)

---

