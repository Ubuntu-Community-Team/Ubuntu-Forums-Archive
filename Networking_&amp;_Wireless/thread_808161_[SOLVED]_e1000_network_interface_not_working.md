---
title: "[SOLVED] e1000 network interface not working"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by putt1ck on 2008-05-26
Hi

Having a problem with an Intel network controller on a Samsung X60 laptop. This worked prior to clean-installing 8.04.

The e1000 module is loaded and lshw gives:
lshw -C network
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

modprobe -r e1000 then modprobe e1000 gives this dmesg output:
[37568.139733] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[37568.139741] Copyright (c) 1999-2006 Intel Corporation.
[37568.140266] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[37568.140290] PCI: Setting latency timer of device 0000:02:00.0 to 64
[37568.194506] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
[37568.214681] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[37568.219594] e1000: probe of 0000:02:00.0 failed with error -5

As I'm also suffering from the iwl3945 intermittent wireless networking issue, any and all suggestions welcome...

---

### Post by putt1ck on 2008-05-27
bump...

---

### Post by putt1ck on 2008-05-27
Thanks to 

[http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid](http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid)

I have found a fix. Just do:

modprobe e1000 eeprom_bad_csum_allow=1

Apparently:

"You might also apply that parameter via modprobe.d or if you are using Debian/Ubuntu as append-line in your bootloader: e1000.eeprom_bad_csum_allow=1 "

But I haven't tried that yet, too busy catching up on my work from our northern office :)

---

