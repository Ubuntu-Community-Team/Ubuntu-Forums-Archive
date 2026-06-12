---
title: "Feisty Ra2570 trouble"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by conorobyrne on 2007-04-20
When I attach the USB Wifi device this is what happens:

```

[  164.526780] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  164.853199] usb 1-1: configuration #1 chosen from 1 choice
[  165.176745] Loading module: rt2x00lib - CVS (N/A) by http://rt2x00.serialmonkey.com.
[  165.190337] Loading module: rt73usb - CVS (N/A) by http://rt2x00.serialmonkey.com.
[  165.458323] usbcore: registered new interface driver rt73usb
[  165.571513] usbcore: registered new interface driver prism54usb
[  165.612053] usbcore: registered new interface driver rt2570
[  166.278348] wmaster0: Selected rate control algorithm 'simple'
[  166.422763] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -32.
[  166.638652] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[  166.643640] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.

```

I'd go look for a solution myself but I don't understand what the problem is. Can anyone shed some light on what's going on here?

The device used to work in edgy. It wasn't exactly reliable though. It managed to connect to the network after three attempts through wlassistant every time though! No luck so far with network manager.

---

