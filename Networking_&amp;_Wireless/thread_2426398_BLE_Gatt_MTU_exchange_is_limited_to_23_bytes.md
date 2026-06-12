---
title: "BLE Gatt MTU exchange is limited to 23 bytes"
date: 2019-09-08
forum: Networking &amp; Wireless
---

### Post by modestid on 2019-09-08
The Raspbian Stretch Lite, Kernel Version: 4.14.52+,  BlueZ Version: 5.43 always specifies 23 bytes as the receive MTU size. When making a Bluetooth LE GATT connection both devices exchange their MTU size. The smallest value of both is used, which dictates the notification data size.  I need to increase the MTU size so I can notify with larger data packets. I've seen that the L2CAP PDU size limits the ATT mtu size, and that the patch "Change default MTU for L2CAP ATT channel" by Andre Guedes was introduced in [Linux 3.6], so I don't know why I'm still limited to 23 bytes. Does anyone have insight into this issue?

---

