---
title: "Connecting to wired ethernet card in Ubuntu"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by sam74 on 2014-08-22
Hello,

I just put together a new machine and I am unable to detect the NIC and use a wired ethernet connection.

Some details.


The NIC: Qualcomm Atheros Killer E2200 gigabit ethernet controller put out by Realtek.  Intel Core i7-4770K processor. I am using Xubuntu 13.04 with Linux release 3.8.0.


the associated driver is 8139too, I believe, which i can see with 'lsmod'

 $ sudo lshw -C network


shows that the Ethernet controller is UNCLAIMED


$ ifconfig 

shows the 'lo' local loopback but no eth0
Any help would be greatly appreciated.

Thank you
Sam

---

### Post by chili555 on 2014-08-22
The driver for your card is probably *alx*. > I am using Xubuntu 13.04 with Linux release 3.8.0.I don't think *alx* is present and covering your device in 3.8.0-xx. I suggest you reinstall 14.04 and your device should work as expected.

---

### Post by sam74 on 2014-08-22
Solved the problem. thank you
_sam_

---

### Post by Kaballasx on 2014-09-13
I have the same problem but wit R8169 - Dlink DGE 560t(pci-e)
But here it states its DGE 528t (pci)

This is a second Ethernet controler.

*-network UNCLAIMED     
       description: Ethernet controller
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:e800(size=256) memory:fe8ff000-fe8fffff memory:fdffc000-fdffffff memory:fe8e0000-fe8effff

it lists every where,

-------------------------------------------------------------------
dmesg | grep r816
[    2.973442] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.973472] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.973485] r8169 0000:02:00.0: (unregistered net_device): region #1 not an MMIO resource, aborting
[    2.973494] r8169 0000:02:00.0: PCI INT A disabled

------------------------------------------------------------------


lsmod | grep 816
r8169                  62190  0

PS Going Out of my mind...

---

### Post by chili555 on 2014-09-13
> **Kaballasx said:**
> I have the same problem but wit R8169 - Dlink DGE 560t(pci-e)
But here it states its DGE 528t (pci)

This is a second Ethernet controler.

*-network UNCLAIMED     
       description: Ethernet controller
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:e800(size=256) memory:fe8ff000-fe8fffff memory:fdffc000-fdffffff memory:fe8e0000-fe8effff

it lists every where,

-------------------------------------------------------------------
dmesg | grep r816
[    2.973442] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.973472] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.973485] r8169 0000:02:00.0: (unregistered net_device): region #1 not an MMIO resource, aborting
[    2.973494] r8169 0000:02:00.0: PCI INT A disabled

------------------------------------------------------------------


lsmod | grep 816
r8169                  62190  0

PS Going Out of my mind...Please post:```
lspci -nn | grep 0200
cat /etc/modules
```Thanks.

---

### Post by Kaballasx on 2014-09-14
02:00.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 06)
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe [14e4:165b] (rev 10)

cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


loop
lp
rtc

Thanks very much for the quick reply

---

### Post by Kaballasx on 2014-09-14
There is no IRQ conflict

02:00.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 06)
	Subsystem: D-Link System Inc DGE-560T PCI Express (x1) Gigabit Ethernet Adapter
	Flags: fast devsel, IRQ 16
	I/O ports at e800 [size=256]
	Memory at fe8ff000 (64-bit, non-prefetchable) [size=4K]
	Memory at fdffc000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at fe8e0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number d6-03-00-00-68-4c-e0-00
	Kernel modules: r8169


 lspci -v | grep IRQ
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 42
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Flags: fast devsel, IRQ 16
	Flags: bus master, fast devsel, latency 0, IRQ 43

---

### Post by chili555 on 2014-09-14
I have googled this extensively:> r8169 0000:02:00.0: (unregistered net_device): region #1 not an MMIO resource, abortingSome of the threads I found also suspect an IRQ problem; you might check:```
dmesg | grep -i irq
```Also, I have the best luck with the BIOS set to auto select IRQs.

Only one thread I found solved the problem. He moved the card to a different PCI slot. Whether that solved an underlying IRQ problem or just better seated the card in its new slot, I don't know. I suggest you try the same.

Finally, several threads suggested a different card.

---

### Post by Kaballasx on 2014-09-14
I changed the slot, the problem still exists.
It was on IRQ 16

Now it is on IRQ 18.
The problem just moves.

The last step is to format and reinstall. I will boot with a live disk and check it out.
This is an HP proliant micro server. Its great for streaming HD 1080P to my 2 Tv's and backing up data.

Thanks for the help.

---

### Post by Kaballasx on 2014-09-14
I have tested it with a live disk. The network card does not even light up. I bought 2 of these since I have 2 micro servers and tested both cards on the machine.
It is the same with both. IRQ issue, it seems like HP only wants to work with their hardware.

Thanks for the assistance.

---

