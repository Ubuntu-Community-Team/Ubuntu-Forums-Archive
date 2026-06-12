---
title: "Excessively slow wifi"
date: 2018-07-29
forum: Networking &amp; Wireless
---

### Post by sssSami on 2018-07-29
I'm about 2-3 meters away from the AP, which is in the same room, yet the download speed it reports in System Monitor fluctuates between 0 KiB/s and 1.5 MiB/s while VLC is streaming video over SMB (and the buffer is empty pretty much constantly). Simply browsing the web is a painful experience. I've been using WiFi on this exact spot with Windows, and seemingly got the full potential out of the wifi card, so surely it's a driver issue.

From lspci:
```
24:00.0 Network controller: Ralink corp. RT3592 Wireless 802.11abgn 2T/2R PCIe
```
I'm connected to an Asus RT-N66U router in AP mode. I also have an RT-AC3200, and despite being *much* further away, works *a lot* better when I tried it just now.

I'd much prefer to be connected to the AP in my room, given the much shorter distance. Also, as mentioned, it worked really well with Windows. So why does it work so poorly in Ubuntu? Is there any way to fix this?

---

