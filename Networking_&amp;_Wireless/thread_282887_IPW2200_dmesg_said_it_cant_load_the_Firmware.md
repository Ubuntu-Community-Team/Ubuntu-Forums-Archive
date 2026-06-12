---
title: "IPW2200 dmesg said it cant load the Firmware"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by a_r_cheraghi on 2006-10-23
I have a big problem and I cant solve it.
By loading the IPW2200 module with modprobe I get this Message form dmesg:

pw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0dmq
ipw2200: Copyright(c) 2003-2006 Intel Corporation
ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
ipw2200: Unable to load firmware: -2
ipw2200: failed to register network device
ACPI: PCI interrupt for device 0000:02:02.0 disabled
ipw2200: probe of 0000:02:02.0 failed with error -5


I copied all the Firmware in the directory lib/firmware.
And Im using the newest ipw2200 driver and the KUbuntu 6.06.
Can somebody help me please!!!!!

Cheers

---

### Post by nacnud on 2006-10-29
I have the same problem after upgrading from Dapper to Edgy.  I've looked around and it seems a few other people do too--but I haven't found the solution yet.

---

