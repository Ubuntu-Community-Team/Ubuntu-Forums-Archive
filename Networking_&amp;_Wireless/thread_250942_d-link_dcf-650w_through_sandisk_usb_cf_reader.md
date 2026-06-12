---
title: "d-link dcf-650w through sandisk usb cf reader"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by jimmyp on 2006-09-04
I am trying to get my 802.11b compact flash card (dcf-650w) to work on my desktop.  I plugged it into a sandisk usb compact flash reader.  When I plug in the reader, dmesg reports it:

[4298838.597000] usb 1-2: new full speed USB device using uhci_hcd and address 4[4298838.696000] scsi1 : SCSI emulation for USB Mass Storage devices
[4298838.697000] usb-storage: device found at 4
[4298838.697000] usb-storage: waiting for device to settle before scanning
[4298843.700000]   Vendor: SanDisk   Model: ImageMate II      Rev: 1.30
[4298843.700000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4298843.709000] usb-storage: device scan complete

but nothing comes up about the wireless card that is plugged into it.  Both lights on the wireless card are on.  I think this card is supported by the prism2 driver and I can modprobe prism2 but the card doesn't show up in the network settings configuration box.

I am testing this on a breezy desktop but if it works I am going to be using it on a dapper laptop.

Thanks.

---

