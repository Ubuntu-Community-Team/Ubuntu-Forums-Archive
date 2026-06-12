---
title: "[SOLVED] TRENDnet TEW-423PI on Intrepid"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by coolbrook on 2008-11-02
This wireless PCI card works out of the box with the rtl8180 driver. but it's slow as molasses.

I'm happy to report there's a dramatic increase in link quality and network speed if the rtl8180 driver is blacklisted and the Win 98 (net8185.inf) driver is used with ndiswrapper. I went from 200Kbps to 4100 downstream according to speedtest.

---

