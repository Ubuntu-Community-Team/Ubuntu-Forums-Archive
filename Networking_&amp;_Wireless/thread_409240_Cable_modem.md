---
title: "Cable modem"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by rcmiv on 2007-04-14
Why does this happen to my usb cable modem periodically?

from /var/log/messages:
```
Apr 14 10:21:07 Daisy kernel: [838895.240664] usb 1-2: USB disconnect, address 45
Apr 14 10:21:07 Daisy kernel: [838895.242942] eth0: unregister 'cdc_ether' usb-0000:00:07.2-2, CDC Ethernet Device
Apr 14 10:21:10 Daisy kernel: [838897.971817] usb 1-2: new full speed USB device using uhci_hcd and address 46
Apr 14 10:21:11 Daisy kernel: [838898.172579] usb 1-2: configuration #1 chosen from 1 choice
Apr 14 10:21:11 Daisy kernel: [838898.180644] eth0: register 'cdc_ether' at usb-0000:00:07.2-2, CDC Ethernet Device, 00:e0:6f:33:e2:8b
Apr 14 10:21:23 Daisy gconfd (myusername-12933): starting (version 2.16.0), pid 12933 user 'myusername'
```

Basically (it appears), the kernel unregisters the usb driver for cdc devices, and then registers it again, dropping the connection to my isp in the process.  This happens several times per day, and takes a widely varying period of time to re-register.

Using 2.6.17-10-generic

Any ideas?

-rcmiv

---

### Post by rcmiv on 2007-04-18
> **rcmiv said:**
> Why does this happen to my cable modem periodically?

from /var/log/messages:
```
Apr 14 10:21:07 Daisy kernel: [838895.240664] usb 1-2: USB disconnect, address 45
Apr 14 10:21:07 Daisy kernel: [838895.242942] eth0: unregister 'cdc_ether' usb-0000:00:07.2-2, CDC Ethernet Device
Apr 14 10:21:10 Daisy kernel: [838897.971817] usb 1-2: new full speed USB device using uhci_hcd and address 46
Apr 14 10:21:11 Daisy kernel: [838898.172579] usb 1-2: configuration #1 chosen from 1 choice
Apr 14 10:21:11 Daisy kernel: [838898.180644] eth0: register 'cdc_ether' at usb-0000:00:07.2-2, CDC Ethernet Device, 00:e0:6f:33:e2:8b
Apr 14 10:21:23 Daisy gconfd (myusername-12933): starting (version 2.16.0), pid 12933 user 'myusername'
```

Basically (it appears), the kernel unregisters the module for the modem, and then registers it again, dropping the connection to my isp in the process.  This happens several times per day, and takes a widely varying period of time to re-register.

Using 2.6.17-10-generic

Any ideas?

-rcmiv

I am still unable to find any explanation for this behavior.  I have recreated the setup I am using with a Feisty Beta live cd, and it behaves the same.

I basically have it set up to act as a router using iptables, and when I first set it up that way, it was not doing this (that I noticed).  Now it disconnects and reconnects several times per day.  Could it be the modem hardware?

Any ideas would be greatly appreciated.

-rcmiv

---

