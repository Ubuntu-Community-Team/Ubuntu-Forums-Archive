---
title: "Looking for a USB Wifi adapter"
date: 2005-09-03
forum: Networking &amp; Wireless
---

### Post by celloandy on 2005-09-03
I'm looking for a USB 802.11g adapter with native (i.e. non-ndiswrapper) drivers.  Anybody have any luck with any of these?

Andrew

---

### Post by numberexhaust on 2005-09-03
You're asking for a miracle.  There are literally no native "g" adapters that actually work.  My best recommendation is to get a good one and use ndiswarpper (and madwifi when it gets better).  I got a netgear WG511T pci card and I use ndiswrapper:  everything works great.

---

### Post by daftmunkie on 2005-09-03
while i wouldn't say it's a miricale yet because I haven't quite got mine up and running, but there is a lot of enthusiasm for a D-Link wireless adapter over here:
[http://ubuntuforums.org/showthread.php?t=53035&highlight=DWL-G122](http://ubuntuforums.org/showthread.php?t=53035&highlight=DWL-G122)
and there's an open source project making drivers, to boot!
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

hope that helps...

---

### Post by cbudden on 2005-09-03
I know its a internal adapter but the IPW2200 works straight "out of the box"

---

### Post by mendicant on 2005-09-03
I've successfully used these:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833158111](http://www.newegg.com/Product/Product.asp?Item=N82E16833158111)

on Ubuntu with the rt2570 USB driver from the same place listed above.  Here's a direct link to the driver package:

[http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b1.tar.gz?download](http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b1.tar.gz?download)

It's a bit big--much wider than others I've seen, but it's got a very cool stiff but flexible USB extension cable, perfect for aligning the dongle.  You can see the cable here:
[http://www.msicomputer.com/product/p_spec.asp?model=US54G&class=com](http://www.msicomputer.com/product/p_spec.asp?model=US54G&class=com)
at the bottom of the page.  It'll stay in whatever shape you put it in (within reason).

---

