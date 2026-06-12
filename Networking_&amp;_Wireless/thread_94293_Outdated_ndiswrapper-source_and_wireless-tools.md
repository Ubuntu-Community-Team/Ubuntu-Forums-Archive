---
title: "Outdated ndiswrapper-source and wireless-tools"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by kristian on 2005-11-23
Just installed kernel 2.6.14.2 and realized that ndiswrapper-source wouldn't make any more, downloaded the latest stable 1.5 from sf.net and that worked.

Later on I tried to scan for wlans and I get this message:
Warning: Driver for device wlan0 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

So my question is simple, why is the ndiswrapper-source only version 1.1 that doesn't work with newer kernels and it also seems that wireless-tools is not compatible with ndiswrapper 1.5. I know that Breezy is a stable release but shouldn't these things be somewhat up to date?

---

