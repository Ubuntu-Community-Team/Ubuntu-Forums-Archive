---
title: "Broadcom"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by gharsh on 2007-03-22
Hello,

I have installed 6.06 and was looking to see if my wireless card will work.  I am assuming not since it is a Broadcom card, but I could not find the specific model listed on the wiki page.  I believe the  model number is BCMWL5 (?).  This is what I have been able to track down.  It is an internal antenna and works fine with windows, but I can't seem to get it to work with Ubuntu.  When I got o enable it, I get an error message.  I'll check again what the message is specifically and post that as well.

Thanks.

---

### Post by bengalsfan74 on 2007-03-22
I don't know about Edgy, but in previous versions, if you ran ndiswrapper, and then loaded the Windows driver it would work.

The bad thing is if you are running anything other than WEP you'll also need to run iwconfig and set it up to use WPA with the proper driver.

This always gave me pains in the past.

---

### Post by chili555 on 2007-03-22
The best way to identify it is to run:```
lspci -v
```Then look for a network controller. Here's mine, for example:```
03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Netgear WG511 Wireless Adapter
        Flags: bus master, medium devsel, latency 56, IRQ 11
        Memory at c4000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
```

Ah! I have a Netgear WG511! Now you can go back to the Wiki, cross-reference your card and install it.

> pains in the pastWell that rhymes with where it gives me pains...

---

