---
title: "TP-Link WN823n-v2 not seen - Ubuntu Mate desktop"
date: 2016-11-04
forum: Networking &amp; Wireless
---

### Post by Catchpole on 2016-11-04
I have used a USB WN823N wifi adapter with Ubuntu Mate and it works OK. Automatically detected.

So I bought another one which is WN823NV2 and tried it in the same computer but its not seen by the operating system.

I downloaded the Linux driver to the "Downloads folder" from the TP-Link website and double clicked on it. It extracted the files but it didn't work.
So I extracted the files into the / root folder but that didn't work either.

Somewhere on the internet I read that I need to use the "make" command but no details were provided as to how to do that or where to put the files.

sudo lsusb gives:
iManufacturer = Realtek 
iProduct = 802.11n NIC

Can anyone help?

---

### Post by chili555 on 2016-11-04
> sudo lsusb gives:
iManufacturer = Realtek 
iProduct = 802.11n NIC
It contains more than that. In fact, the usb.id that you omitted, something like 1234:ab56, is what we *really* need. Please post all of the details.

---

