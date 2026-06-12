---
title: "dlink AX1800 Wi-Fi 6 USB 3.0 Adapter DWA-X1850"
date: 2021-04-09
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2021-04-09
Anyone know what chipset this uses?
[https://www.dlink.com/en/products/dwa-x1850-ax1800-wi-fi-6-usb-30-adapter](https://www.dlink.com/en/products/dwa-x1850-ax1800-wi-fi-6-usb-30-adapter)

---

### Post by jeremy31 on 2021-04-09
My guess would be a Qualcomm Atheros chipset as it has been a long time since Intel released something USB

---

### Post by bjlockie on 2021-04-13
The DLink DWA-X1850 - AX1800 Wi-Fi 6 USB 3.0 Adapter uses a Realtek chipset according to DLink.
I hope Mediatek or Atheros or Intel does. :-)
I think Realtek drivers suck.

---

### Post by morrownr on 2021-04-15
> **bjlockie said:**
> The DLink DWA-X1850 - AX1800 Wi-Fi 6 USB 3.0 Adapter uses a Realtek chipset according to DLink.
I think Realtek drivers suck.

There are three very good reasons for Linux users to avoid that device:

1. d-link, like tp-link, does a really poor job of supporting Linux users. They change chipsets in their products while keeping the same model information making it difficult for us to know what we are getting with any degree of certainty and they tend to use chipsets that are not well supported for use on Linux.

2. Realtek USB WiFi drivers suck.

3. Did I mention that Realtek USB WiFi drivers suck?

For information on USB WiFi adapters that use in-kernel drivers:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

That site currently has 56 links to WiFi adapters that use in-kernel drivers. The adapters range in capability from N150 to AC1200 and in price from $4 to $60.

---

