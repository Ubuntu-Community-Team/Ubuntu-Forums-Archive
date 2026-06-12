---
title: "Cnet611 (atmel) issues"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Tom_K on 2007-06-12
Hi!

I'm having a bit of an issue getting my Cnet 611 - USB device to work with Ubuntu.
As I have been told this device uses the atmel driver set, so the atmel-firmware has been installed,
however it still will not work.

I may, however, have found a reason for this problem.

According to the atmel driver website ([http://atmelwlandriver.sourceforge.net/](http://atmelwlandriver.sourceforge.net/)),
the device CNUSB-611 has vendor id: 0x03eb and product id: 0x7603 

However, reviewing my hardware information in Ubuntu, this is what comes up from the usb device:

Vendor ID: 0x1371 product id: 0x1

Okay, so far, so good. But as far as I can tell, this pid and vid isn't available in any of the cards that the atmel driver recognizes. Question is: Where do I go from here? Is there any way to either get Ubuntu to recognize the card, or is it a lost cause?

Looking forward to your response!

---

