---
title: "Linksys PCMCIA wireless not working after Hardy upgrade"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by irotas on 2008-05-04
This morning I upgraded from Gutsy to Hardy and (just as happened when I upgraded from Feisty to Gutsy) suddenly my Linksys PCMCIA won't work anymore.

I discussed this problem previously on the mailing list and was able to resolve it for Gutsy:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126619.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126619.html)

Unfortunately, the fix I found before is no longer working.

From dmesg:
[   30.912745] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   30.912752] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   30.912843] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   30.912856] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   30.912866] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   30.912880] acx: found ACX111-based wireless network card at 0000:03:00.0, irq:11, phymem1:0x54020000, phymem2:0x54000000, mem1:0xf8a44000, mem1_size:8192, mem2:0xf8b40000, mem2_size:131072
[   30.913892] acx: loading firmware for acx1111 chipset with radio ID 16
[   30.954599] acx: firmware image 'acx/1.2.1.34/tiacx111c16' was not provided. Check your hotplug scripts
[   30.959017] acx: firmware image 'acx/1.2.1.34/tiacx111' was not provided. Check your hotplug scripts
[   30.959024] acx: reset_dev() FAILED
[   30.959064] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   30.971882] acx_pci: probe of 0000:03:00.0 failed with error -5

From lspci:
03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
   Subsystem: Linksys WPC54G Ver.2 802.11G PC Card
   Flags: medium devsel, IRQ 11
   Memory at 54020000 (32-bit, non-prefetchable) [size=8K]
   Memory at 54000000 (32-bit, non-prefetchable) [size=128K]
   Capabilities: [40] Power Management version 2

Anyone else having the same problem? Is Linksys wireless support really that bad on Linux? Is there another brand card I should buy?

Thanks,
Adam

---

### Post by irotas on 2008-05-04
Well I took a shot in the dark and installed linux-restricted-modules-2.6.24-16-386 version 2.6.24.12-16.34, and amazingly that seems to have done the trick. Must be my lucky day!

As a side note, this also fixed my problems with the 'nvidia' driver.

Hope this helps someone :)

---

### Post by Paris Heng on 2008-05-04
> **irotas said:**
> Well I took a shot in the dark and installed linux-restricted-modules-2.6.24-16-386 version 2.6.24.12-16.34, and amazingly that seems to have done the trick. Must be my lucky day!

As a side note, this also fixed my problems with the 'nvidia' driver.

Hope this helps someone :)

Please share any relevant links to your problems. Thanx.

---

