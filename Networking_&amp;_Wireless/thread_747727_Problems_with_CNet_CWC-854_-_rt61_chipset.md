---
title: "Problems with CNet CWC-854 - rt61 chipset"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by ymgve on 2008-04-06
I'm having trouble getting my CNet CWC-854 PCMCIA card to work in Ubuntu. Right now I'm running 8.04, but I had the same problems in 7.10 and Backtrack beta3 too, so it's probably unrelated to the distro version.

The default drivers give me these dmesg messages:
```

[  544.409295] pccard: CardBus card inserted into slot 0
[  544.600264] PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
[  544.600278] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 21 (level, low) -> IRQ 16
[  544.600291] PCI: Setting latency timer of device 0000:09:00.0 to 64
[  544.605132] phy0 -> rt61pci_init_eeprom: Error - Invalid RF chipset detected.
[  544.605137] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[  544.605153] ACPI: PCI interrupt for device 0000:09:00.0 disabled

```

lspci -vvv dump:
```

09:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
	Subsystem: RaLink Unknown device 2561
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 40000000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

```

I've tried using ndiswrapper on the Windows drivers for this card, but this results in the PC locking up when inserting the card or booting up with the card inserted. I've also tried the latest version of the legacy rt61 drivers from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads) with the same result for the most part. There was a few times it didn't crash, and then it resulted in a message about the firmware missing - even though the firmware files were stored in the proper locations.

Anyone have experienced something similar, or got an idea how I can fix this?

---

### Post by ymgve on 2008-04-06
Managed to recreate the previously mentioned situation - log of the debug build of the rt61 legacy driver:

dmesg
```

[  375.757967] rt61: 1.1.0 CVS 2008040617 http://rt2x00.serialmonkey.com
[  375.757972] rt61: ==> rt61_module_init
[  375.758675] rt61: ===> rt61_pci_probe
[  375.758702] PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
[  375.758714] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 21 (level, low) -> IRQ 16
[  375.758718] rt61: Vendor=0x1814, Product=0x302
[  375.758734] rt61: wlan%d: at 0x40000000, VA 0xf8c30000, IRQ 16
[  375.758818] rt61: --> PortCfgInit
[  375.758819] rt61: <-- PortCfgInit
[  375.758822] rt61: country code=0/0, RFIC=1, PHY mode=0, support 11 channels
[  375.758825] channel #0
[  375.758827] channel #0
[  375.758828] channel #0
[  375.758829] channel #0
[  375.758831] channel #0
[  375.758832] channel #0
[  375.758833] channel #0
[  375.758835] channel #0
[  375.758836] channel #0
[  375.758837] channel #0
[  375.758839] channel #0
[  375.758843] rt61: ===> NICLoadFirmware
[  375.838838] rt61: NICLoadFirmware OK: CRC = 0xac30 ver=0.8
[  376.836279] rt61: NICLoadFirmware: MCU is not ready
[  376.836281] 
[  376.836282] 
[  376.836289] rt61: <=== NICLoadFirmware (status=1)
[  376.836292] rt61: Could not load firmware! (is firmware file installed?)
[  376.836312] ACPI: PCI interrupt for device 0000:09:00.0 disabled
[  376.836314] rt61: <=== rt61_pci_probe (status: 1)

```

/var/log/messages
```

Apr  7 03:27:33 laptop-foo kernel: [  363.033957] pccard: CardBus card inserted into slot 0
Apr  7 03:27:46 laptop-foo kernel: [  375.757967] rt61: 1.1.0 CVS 2008040617 http://rt2x00.serialmonkey.com
Apr  7 03:27:46 laptop-foo kernel: [  375.758702] PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
Apr  7 03:27:46 laptop-foo kernel: [  375.758714] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 21 (level, low) -> IRQ 16
Apr  7 03:27:46 laptop-foo kernel: [  375.758825] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758827] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758828] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758829] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758831] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758832] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758833] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758835] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758836] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758837] channel #0
Apr  7 03:27:46 laptop-foo kernel: [  375.758839] channel #0
Apr  7 03:27:47 laptop-foo kernel: [  376.836281] 
Apr  7 03:27:47 laptop-foo kernel: [  376.836282] 
Apr  7 03:27:47 laptop-foo kernel: [  376.836312] ACPI: PCI interrupt for device 0000:09:00.0 disabled

```

/var/log/debug
```

Apr  7 03:27:46 laptop-foo kernel: [  375.757972] rt61: ==> rt61_module_init
Apr  7 03:27:46 laptop-foo kernel: [  375.758675] rt61: ===> rt61_pci_probe
Apr  7 03:27:46 laptop-foo kernel: [  375.758718] rt61: Vendor=0x1814, Product=0x302
Apr  7 03:27:46 laptop-foo kernel: [  375.758734] rt61: wlan%d: at 0x40000000, VA 0xf8c30000, IRQ 16
Apr  7 03:27:46 laptop-foo kernel: [  375.758818] rt61: --> PortCfgInit
Apr  7 03:27:46 laptop-foo kernel: [  375.758819] rt61: <-- PortCfgInit
Apr  7 03:27:46 laptop-foo kernel: [  375.758822] rt61: country code=0/0, RFIC=1, PHY mode=0, support 11 channels
Apr  7 03:27:46 laptop-foo kernel: [  375.758843] rt61: ===> NICLoadFirmware
Apr  7 03:27:47 laptop-foo kernel: [  375.838838] rt61: NICLoadFirmware OK: CRC = 0xac30 ver=0.8
Apr  7 03:27:47 laptop-foo kernel: [  376.836279] rt61: NICLoadFirmware: MCU is not ready
Apr  7 03:27:47 laptop-foo kernel: [  376.836289] rt61: <=== NICLoadFirmware (status=1)
Apr  7 03:27:47 laptop-foo kernel: [  376.836314] rt61: <=== rt61_pci_probe (status: 1)

```

---

