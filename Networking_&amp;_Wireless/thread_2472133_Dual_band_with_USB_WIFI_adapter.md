---
title: "Dual band with USB WIFI adapter"
date: 2022-02-18
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2022-02-18
Hi,

I have a USB adapater for my Wifi connection that support dual band. However, till now I'm able to make it work onlly under 5Ghz or 2.4Ghz.
Any idea what should I do to make ubuntu use both bands at the same time ?

Adapater support till 1300 Mbps and it's an AC1300S using the chipset [FONT=monospace][COLOR=#000000]RTL88x2bu (lsusb result).

thank you
[/COLOR]
[/FONT]

---

### Post by chili555 on 2022-02-18
> **alain.roger said:**
> Any idea what should I do to make ubuntu use both bands at the same time ?Even if it were possible, why?

The 2.4 gHz band is always slower than 5 gHz. If your device is capable of a strong connection at 5 gHz, why not connect to it exclusively?

If your idea is that you are getting, say 300 Mbps from the 5 gHz band but 75 Mbps from the 2.4 gHz band and, if you could run both at the same time, you could get 375 Mbps, then I know of no way to do so, even if you used two devices.

In my opinion, the feature in routers that autoselects 2.4 or 5 gHz and attempts to switch your connection on the fly, is terrible and causes more problems than it fixes.

---

### Post by morrownr on 2022-02-20
> **alain.roger said:**
> Hi,

Any idea what should I do to make ubuntu use both bands at the same time ?



It can't work. I am not aware of any USB WiFi adapters that have two radios. To be able to operate on both bands at the same time, you need two radios. One for 2.4 GHz and one for 5 GHz. Dual band access points/routers have two radios inside.

For additional information about USB WiFi adapters for use on Linux:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Regards

---

