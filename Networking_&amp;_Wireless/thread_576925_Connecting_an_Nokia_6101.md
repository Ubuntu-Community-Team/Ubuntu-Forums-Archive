---
title: "Connecting an Nokia 6101"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by Nighto on 2007-10-15
Hi,

I want to connect a Nokia 6101 mobile to my Ubuntu Gutsy laptop. Unlike other things i connect on usb, such as external disks and pendrives that mount automatically, the cellphone doesn't. I looked at dmesg, when i connect the 6101 it spits out like this:
```

[ 1631.252000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[ 1631.372000] usb 1-2: device descriptor read/64, error -71
[ 1631.596000] usb 1-2: device descriptor read/64, error -71
[ 1631.812000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[ 1631.932000] usb 1-2: device descriptor read/64, error -71
[ 1632.156000] usb 1-2: device descriptor read/64, error -71
[ 1632.372000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[ 1632.780000] usb 1-2: device not accepting address 4, error -71
[ 1632.892000] usb 1-2: new low speed USB device using uhci_hcd and address 5
[ 1633.300000] usb 1-2: device not accepting address 5, error -71
[ 1635.684000] usb 1-2: new low speed USB device using uhci_hcd and address 6
[ 1635.804000] usb 1-2: device descriptor read/64, error -71
[ 1636.028000] usb 1-2: device descriptor read/64, error -71
[ 1636.244000] usb 1-2: new low speed USB device using uhci_hcd and address 7
[ 1636.364000] usb 1-2: device descriptor read/64, error -71
[ 1636.588000] usb 1-2: device descriptor read/64, error -71
[ 1636.804000] usb 1-2: new low speed USB device using uhci_hcd and address 8
[ 1637.212000] usb 1-2: device not accepting address 8, error -71
[ 1637.324000] usb 1-2: new low speed USB device using uhci_hcd and address 9
[ 1637.732000] usb 1-2: device not accepting address 9, error -71
[ 2456.056000] usb 1-2: new low speed USB device using uhci_hcd and address 10
[ 2456.180000] usb 1-2: device descriptor read/64, error -71
[ 2456.404000] usb 1-2: device descriptor read/64, error -71
[ 2456.620000] usb 1-2: new low speed USB device using uhci_hcd and address 11
[ 2456.740000] usb 1-2: device descriptor read/64, error -71
[ 2456.964000] usb 1-2: device descriptor read/64, error -71
[ 2457.180000] usb 1-2: new low speed USB device using uhci_hcd and address 12
[ 2457.588000] usb 1-2: device not accepting address 12, error -71
[ 2457.700000] usb 1-2: new low speed USB device using uhci_hcd and address 13
[ 2458.108000] usb 1-2: device not accepting address 13, error -71

```

Also, lsusb is empty:
```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

The mobile and the cable are good, since they work on that Microsoft's OS.

Any suggestions?

Thanks in advance.

---

