---
title: "Cell internet card no longer /dev/ttyACM0 in Gutsy?"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by glibdud on 2008-02-18
I'm running Xubuntu on an aging Dell (Latitude CPi D300XT), and trying to get a Pantech PX500 PCMCIA "mobile broadband card" working on Sprint's network. I originally had Feisty installed, and following some tutorials found here and elsewhere, I got it to work wonderfully. But for a variety of reasons, I upgraded to Gutsy.

Under Feisty, when I popped the card in, is came up as /dev/ttyACM0. Now, when I insert it, I get the following:

```
[  324.592000] pccard: CardBus card inserted into slot 1
[  325.844000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[  325.852000] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
[  325.852000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[  325.852000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[  325.852000] ohci_hcd 0000:05:00.0: OHCI Host Controller
[  325.856000] ohci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 2
[  325.856000] ohci_hcd 0000:05:00.0: irq 11, io mem 0x2c000000
[  325.944000] usb usb2: configuration #1 chosen from 1 choice
[  325.944000] hub 2-0:1.0: USB hub found
[  325.944000] hub 2-0:1.0: 1 port detected
[  326.048000] PCI: Enabling device 0000:05:00.1 (0000 -> 0002)
[  326.048000] ACPI: PCI Interrupt 0000:05:00.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[  326.048000] PCI: Setting latency timer of device 0000:05:00.1 to 64
[  326.048000] ohci_hcd 0000:05:00.1: OHCI Host Controller
[  326.052000] ohci_hcd 0000:05:00.1: new USB bus registered, assigned bus number 3
[  326.052000] ohci_hcd 0000:05:00.1: irq 11, io mem 0x2c001000
[  326.140000] usb usb3: configuration #1 chosen from 1 choice
[  326.140000] hub 3-0:1.0: USB hub found
[  326.140000] hub 3-0:1.0: 1 port detected
[  330.080000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[  330.292000] usb 2-1: configuration #1 chosen from 1 choice
[  331.796000] usbcore: registered new interface driver usbserial
[  331.808000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  331.812000] usbcore: registered new interface driver usbserial_generic
[  331.812000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  331.856000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[  331.860000] airprime 2-1:1.0: airprime converter detected
[  331.860000] usb 2-1: airprime converter now attached to ttyUSB0
[  331.864000] usb 2-1: airprime converter now attached to ttyUSB1
[  331.864000] usb 2-1: airprime converter now attached to ttyUSB2
[  331.864000] airprime 2-1:1.1: airprime converter detected
[  331.864000] usb 2-1: airprime converter now attached to ttyUSB3
[  331.868000] usb 2-1: airprime converter now attached to ttyUSB4
[  331.868000] usb 2-1: airprime converter now attached to ttyUSB5
[  331.868000] airprime 2-1:1.2: airprime converter detected
[  331.872000] usb 2-1: airprime converter now attached to ttyUSB6
[  331.872000] usb 2-1: airprime converter now attached to ttyUSB7
[  331.872000] usb 2-1: airprime converter now attached to ttyUSB8
[  331.872000] usbcore: registered new interface driver airprime
[  332.316000] usbcore: registered new interface driver cdc_acm
[  332.316000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
```

No /dev/ttyACM* modules exist, and I've tried all 9 of those /dev/ttyUSB[0-8] devices to no avail. The proper modules appear to be loaded... any idea what changed between the releases?

Any advice appreciated.

---

