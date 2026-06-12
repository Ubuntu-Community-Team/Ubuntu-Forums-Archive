---
title: "BCM43142: Bluetooth not working, WIFI is ok"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by Mustafa_Khan on 2014-03-26
So I have a Wifi/BT combo BCM43142 card in my Thinkpad E545.  The wifi worked out of the box but the bluetooth doesn't detect any devices for pairing. Has anybody got any information on how to solve this issue?

I get the following message with dmesg | grep Bluetooth

```
[   13.907597] Bluetooth: Core ver 2.16
[   13.907625] Bluetooth: HCI device and connection manager initialized
[   13.907635] Bluetooth: HCI socket layer initialized
[   13.907638] Bluetooth: L2CAP socket layer initialized
[   13.907645] Bluetooth: SCO socket layer initialized
[   14.027182] Bluetooth: can't load firmware, may not work correctly
[   16.859553] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.859558] Bluetooth: BNEP filters: protocol multicast
[   16.859571] Bluetooth: BNEP socket layer initialized
[   16.861552] Bluetooth: RFCOMM TTY layer initialized
[   16.861567] Bluetooth: RFCOMM socket layer initialized
[   16.861570] Bluetooth: RFCOMM ver 1.11
[  107.742206] Bluetooth: can't load firmware, may not work correctly
[  111.761058] Bluetooth: can't load firmware, may not work correctly
[  121.511668] Bluetooth: can't load firmware, may not work correctly
[  231.418576] Bluetooth: can't load firmware, may not work correctly
[  274.141911] Bluetooth: can't load firmware, may not work correctly
[  360.173275] Bluetooth: can't load firmware, may not work correctly
[  410.379069] Bluetooth: can't load firmware, may not work correctly
```

---

