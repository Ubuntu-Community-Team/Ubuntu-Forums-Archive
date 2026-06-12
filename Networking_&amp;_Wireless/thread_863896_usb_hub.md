---
title: "usb hub"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by kimting2008 on 2008-07-18
I have installed the ubuntu 8.04 on the vmaware on my iMAC and attached a USB hub to the iMAC.

On port 1 of the USB hub, I have attached a USB to RSR232 adaptor connected to my router console 

On port 2 of the USB hub, I have attahced a USB to Ethernet adaptor connected to my router as well.

Th problem I have been experiencing is just either one of them works at the same time. I cannot work with both of them at the same time.

Can anyone has idea what is going on?

cdrom$ dmesg | grep eth
[196723.032023] Driver 'sr' needs updating - please use bus_type methods
[196723.093199] Driver 'sd' needs updating - please use bus_type methods
[196723.218829] eth0: registered as PCnet/PCI II 79C970A
[196803.640230] eth0: link up
[196870.205538] eth1: register 'dm9601' at usb-0000:00:07.2-1, Davicom DM9601 USB Ethernet, 00:60:6e:af:5e:be
[196870.433277] eth1: link up, 100Mbps, half-duplex, lpa 0x0081
[197236.147383] eth1: unregister 'dm9601' usb-0000:00:07.2-1, Davicom DM9601 USB Ethernet
[197660.365032] eth1: register 'dm9601' at usb-0000:00:07.2-1, Davicom DM9601 USB Ethernet, 00:60:6e:af:5e:be
[197660.430637] eth1: link up, 100Mbps, half-duplex, lpa 0x0081
[197818.082231] eth1: unregister 'dm9601' usb-0000:00:07.2-1, Davicom DM9601 USB Ethernet


:/cdrom$ dmesg | grep tty
[196717.469849] console [tty0] enabled
[196719.600486] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[196719.600708] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[196719.601741] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[196719.602082] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[196799.353358] audit(1216436964.344:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4832 profile="/usr/sbin/cupsd" namespace="default"
[197246.559510] usb 1-1: pl2303 converter now attached to ttyUSB0
[197636.837531] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[197826.395456] usb 1-1: pl2303 converter now attached to ttyUSB0

---

