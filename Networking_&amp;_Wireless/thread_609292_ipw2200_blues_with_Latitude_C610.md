---
title: "ipw2200 blues with Latitude C610"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by roazena on 2007-11-10
I had the Broadcom 43xx-based cardbus wifi adapter which was working acceptably, but recently received an Intel Pro wifi mini-PCI card which would free up the cardbus slot. When I installed it, unfortunately Ubuntu would not connect to it whether or not the Broadcom card was installed. dmesg | grep ipw gave the "can't find firmware" error:
```
[   30.652000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   30.652000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   30.652000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   30.652000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   31.660000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   31.660000] ipw2200: Unable to load firmware: -2
[   31.660000] ipw2200: failed to register network device
[   31.660000] ACPI: PCI interrupt for device 0000:02:03.0 disabled
[   31.660000] ipw2200: probe of 0000:02:03.0 failed with error -5
```
To make sure I wasn't just tempting fate by installing a card that wasn't explicitly made for the C610, I booted up Windows and installed the driver from Intel's site at which point it worked fine.

As a second test, I booted the laptop from the Gutsy liveCD that just came in the mail this afternoon. While it didn't connect automagically (there being several wifi networks in the neighborhood), it was available from the nm applet and connection was simple. I'm using it right now, as a matter of fact:
```
[  227.012000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  227.080000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[  227.080000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  227.080000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[  227.080000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
```
The only other difference of interest I note is that the dmesg for the liveCD uses the generic kernel and the laptop's own install uses the 386 kernel.

So, I can only conclude something's borked in my installation (a laptop which was upgraded from Feisty to Gutsy through the usual process). What should I check and compare between the liveCD which recognizes the ipw and installs the firmware/driver, and the installation which does neither?

UPDATE: SOLVED! Apparently the ipw2200 stuff isn't available for the 386 kernel which I didn't realize was the default on my laptop. Editing /boot/grub/menu.lst to default to the 'generic' kernel automagically made the system able to load the firmware for the internal card and it's working like a charm now.

---

