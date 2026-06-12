---
title: "Ext. serial modem via USB-&gt;serial adapter"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by pkoebbe on 2005-10-21
Has anyone had any success connecting an external serial modem via a USB->serial adapter  in Breezy?  I tried last night with a CreativeLabs ModemBlaster and it almost worked, but not quite.  The kernel modules pl2303.ko and usbserial.ko were loaded when the adapter was plugged in, and /dev/ttyUSB0 was created automatically.  I symlinked /dev/modem to /dev/ttyUSB0 and in KPPP queried the modem.  It acted like it found it, but the results were less than meaningful.  In each box marked ATSn, the "result" was "ATSn".  Or ATIn...I can't remember now what the screen looks like.

I plugged the modem into a serial port on another computer (with Hoary on it) and it worked just fine.  I'm trying to get it to work on my notebook, which doesn't have a serial port.  Any help appreciated very much.

Peace,
Phillip

---

