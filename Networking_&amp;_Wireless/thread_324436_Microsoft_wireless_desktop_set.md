---
title: "Microsoft wireless desktop set"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by Kim Ming Yap on 2006-12-23
I have bought a Microsoft wireless desktop set (keyboards + mouse) and it is connected to my PC (X64 AMD dual core) through a receiver to the USB port. I have set the keyboard in Ubuntu Preference to Microsoft Wireless. Problem is sometimes the keyboard and mouse freezes. I unplug the receiver from the USB port and replug it and it works. Problem is it happen quite frequent. Please advice. ](*,)

Here is the logs:

Dec 23 18:40:41 Ubuntu gconfd (root-7032): starting (version 2.16.0), pid 7032 user 'root'
Dec 23 18:40:41 Ubuntu gconfd (root-7032): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 23 18:40:41 Ubuntu gconfd (root-7032): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Dec 23 18:40:41 Ubuntu gconfd (root-7032): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec 23 18:40:41 Ubuntu gconfd (root-7032): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec 23 18:40:41 Ubuntu gconfd (root-7032): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Dec 23 18:43:04 Ubuntu kernel: [ 2576.721386] usb 1-8: USB disconnect, address 4
Dec 23 18:43:08 Ubuntu kernel: [ 2578.718751] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
Dec 23 18:43:09 Ubuntu kernel: [ 2579.026352] usb 1-8: new low speed USB device using ohci_hcd and address 5
Dec 23 18:43:09 Ubuntu kernel: [ 2579.133841] usb 1-8: configuration #1 chosen from 1 choice
Dec 23 18:43:09 Ubuntu kernel: [ 2579.140374] input: Microsft Microsoft Wireless Optical Desktop® 2.20 as /class/input/input6
Dec 23 18:43:09 Ubuntu kernel: [ 2579.140406] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop® 2.20] on usb-0000:00:0b.0-8
Dec 23 18:43:09 Ubuntu kernel: [ 2579.158425] input: Microsft Microsoft Wireless Optical Desktop® 2.20 as /class/input/input7
Dec 23 18:43:09 Ubuntu kernel: [ 2579.158513] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop® 2.20] on usb-0000:00:0b.0-8

Dec 23 18:47:11 Ubuntu gconfd (root-7032): GConf server is not in use, shutting down.
Dec 23 18:47:11 Ubuntu gconfd (root-7032): Exiting
Dec 23 18:47:47 Ubuntu kernel: [ 2718.912776] usb 1-8: USB disconnect, address 5
Dec 23 18:47:51 Ubuntu kernel: [ 2720.910142] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
Dec 23 18:47:51 Ubuntu kernel: [ 2721.217744] usb 1-8: new low speed USB device using ohci_hcd and address 6
Dec 23 18:47:52 Ubuntu kernel: [ 2721.325476] usb 1-8: configuration #1 chosen from 1 choice
Dec 23 18:47:52 Ubuntu kernel: [ 2721.331992] input: Microsft Microsoft Wireless Optical Desktop® 2.20 as /class/input/input8
Dec 23 18:47:52 Ubuntu kernel: [ 2721.332024] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop® 2.20] on usb-0000:00:0b.0-8
Dec 23 18:47:52 Ubuntu kernel: [ 2721.349558] input: Microsft Microsoft Wireless Optical Desktop® 2.20 as /class/input/input9
Dec 23 18:47:52 Ubuntu kernel: [ 2721.349645] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop® 2.20] on usb-0000:00:0b.0-8
Dec 23 18:48:16 Ubuntu gconfd (root-7411): starting (version 2.16.0), pid 7411 user 'root'
Dec 23 18:48:16 Ubuntu gconfd (root-7411): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 23 18:48:16 Ubuntu gconfd (root-7411): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Dec 23 18:48:16 Ubuntu gconfd (root-7411): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec 23 18:48:16 Ubuntu gconfd (root-7411): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec 23 18:48:16 Ubuntu gconfd (root-7411): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

---

### Post by pherseu on 2006-12-27
I'm thinking to buy this set... Do you recommend it (to use in a Ubuntu system)? Found a solution? :-)

---

