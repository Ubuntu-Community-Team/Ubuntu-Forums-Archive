---
title: "IORemap fail on inserting wireless cards"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by smacky_wolf on 2007-03-23
Hi all,

I'm having some problems with inserting wireless cards into my laptop, a Compaq Presario V2000 (specifically, V267AU). 

Every time I plug a card in, PCMCIA or Mini-PCI, the card simply does not work. The drivers are all installed correctly, and everything else is working fine. dmesg tells me thus:
```

[17257143.348000] pccard: CardBus card inserted into slot 0
[17257143.348000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 185
[17257143.348000] RT61: Vendor = 0x1814, Product = 0x0302
[17257143.508000] Loading module: rt61pci - CVS (N/A) by http://rt2x00.serialmonkey.com.
[17257143.508000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 185
[17257143.508000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17257143.508000] rt61pci->rt61pci_alloc_dev: Error - Ioremap failed.
[17257143.508000] rt61pci->rt61pci_probe: Error - Failed to allocate device.
[17257143.508000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[17257143.508000] rt61pci: probe of 0000:06:00.0 failed with error -12
```

Not sure what this means. But I would like to know if there is anything I can do at a software level, because (from memory) I don't get any sort of problem like this under WinXP. I've completely ousted Windows from this machine, so there's not really any other options.

Any help would be much appreciated.

---

