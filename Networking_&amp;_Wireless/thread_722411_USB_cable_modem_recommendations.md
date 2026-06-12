---
title: "USB cable modem recommendations?"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by David J Bush on 2008-03-12
I want to get a USB cable modem with FireWire capability to run under i386 Kubuntu 7.10. This is what the ComCast representative told me I would need for a wireless installation. But they don't do Linux. They will install the wireless router, and this modem will receive the FireWire signal and send it to my machine via USB. This will be a 6 mbps connection. I seek recommendations on which make and model would provide a painless installation procedure. Any advice or reference to where I can get more info would be greatly appreciated. Thanks very much!

---

### Post by kidders on 2008-03-13
Hi there,

Unless of course you've already bought a USB modem, my advice is _don't_! If we assume that your modem will get to use 100% of the theoretical maximum bandwidth of a standard USB port (which is impossible), and that there will be no need to use any of that bandwidth for flow control & device management (which is also impossible), then you *might* be able to get your internet connection to operate at 6Mbps over a USB interface.

If the modem is a USB2 modem, then bandwidth will be less of an issue, but you'll still have to contend with unnecessarily CPU-intensive internet access and poor open source USB modem support.

In my opinion, unless you have a very good reason for not doing so (like having already bought a USB modem!), I would recommend connecting your modem to your PC with an Ethernet cable. Involving USB is unnecessary, really.

**Edit:** Incidentally... what are you planning on doing with the firewire port? Do you need high-speed network disk access or something?

---

