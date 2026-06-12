---
title: "Usb adapter tp-link tl-8200nd"
date: 2019-03-22
forum: Networking &amp; Wireless
---

### Post by xtunsy on 2019-03-22
good, I bought an ADAPTER TP-LINK TL-8200ND chipset  rtl8192cu adapter How can I make it work in Ubuntu 18.08? serving in monitor mode and if you can injection of traffic?

---

### Post by chili555 on 2019-03-22
Does the hardware and driver combination support monitor mode? Find out from the terminal:```
iw list
```Do you see this?> 
Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * [COLOR="#FF0000"]monitor[/COLOR]
		 * P2P-client
		 * P2P-GO
		 * P2P-device

If not, there is nothing we can do. A different device might be in order.

---

