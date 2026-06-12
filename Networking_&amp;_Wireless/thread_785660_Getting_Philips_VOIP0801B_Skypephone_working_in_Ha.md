---
title: "Getting Philips VOIP0801B Skypephone working in Hardy?"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Sealbhach on 2008-05-07
This thing here I have  - [Amazon page]("http://www.amazon.co.uk/Philips-VOIP8010-Compatible-Internet-Telephone/dp/tech-data/B000JOZWXC/ref=de_a_smtd")

I'd like to be able to run it in Linux, but it came with its own installation CD so might be a big job to configure it.

If I do sudo dmesg I get:

> [ 3420.739490] usb 5-1: new full speed USB device using uhci_hcd and address 5
[ 3420.896720] usb 5-1: configuration #1 chosen from 1 choice
[ 3421.036526] input: PHILIPS PHILIPS VOIP080 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.3/input/input13
[ 3421.076024] input,hidraw1: USB HID v1.00 Device [PHILIPS PHILIPS VOIP080] on usb-0000:00:1d.0-1


If that's any help.



.

---

### Post by Sealbhach on 2008-06-04
Just for the record, this works fine now.

I had to go into the Settings in the Skype display box, and select this device - which it detected.

Also, I tweaked around with the settings in Alsamixer until I got it working.

.

---

