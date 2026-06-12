---
title: "Problem with WUSB54GC wireless card randomly disconnecting"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Neural_Overload on 2008-02-12
My WUSB54GC wifi dongle randomly disconnects and will not come back. When I reboot after the card has disconnected, upon boot an error pops up and when I unplug it the error stops. I did a dmesg earlier today when the card disconnected:```
[ 3989.076000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 3989.176000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[ 3991.732000] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[ 4016.600000] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
```

---

### Post by rubing on 2008-07-05
I get the same stupid error.  It's always the same stupid problems with Linux.  I can't believe I wasted time trying it out again...even going to the store and buying a supposedly compatible wifi adaptor.  Good grief!

---

### Post by rubing on 2008-07-05
OK, I just installed ndiswrapper and am now using the windows driver, which seems to be working...keeping my fingers crossed.

---

### Post by rubing on 2008-07-07
Things are better, yet computer still occasionally freezes.  I do not reccomend this USB Dongle

---

