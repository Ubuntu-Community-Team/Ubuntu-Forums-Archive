---
title: "Which wrapper"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by cliff01 on 2007-03-18
Do I need ndiswrapper-1.8 or just ndiswrapper to get my usb wireless (Linksys WUSB54G Vs.1) up and running? Where are some diffinitive instructions to help me?
Thanks! Very nooB

---

### Post by Floppyjoe on 2007-03-18
> **cliff01 said:**
> Do I need ndiswrapper-1.8 or just ndiswrapper to get my usb wireless (Linksys WUSB54G Vs.1) up and running? Where are some diffinitive instructions to help me?
Thanks! Very nooB

I found this information on the ndiswrapper site at sourceforge.
> Card: Linksys #[WUSB54Gv1], 802.11b/g, USB 2.0 -- [link here|List#WUSB54G]

    * Chipset: Prism54
    * usbid: 5041:2234
    * Driver: Linksys Windows XP driver [174]
    * Other: Works smoothly, of course ;) - this is the device the USB extension was originally developed for. WEP is running, WPA is supported using wpa_supplicant 0.2.5. No problems with both 1.1 and 2.0 host controllers. As with many other USB devices, no success with 2.4 kernels so far. Try to use 2.6.7 or better. There is a native driver for Prism54 that is working on USB support. View its status at Prism54.org
    * Other: Works with latest Windows Driver from linksys.com. No success with 2.4 kernels (even with 8k stack). Works with kernel 2.6.11 and 2.6.12. Works smoothly with 2.6.12 and ndiswrapper 1.14.
    * Other: Driver from Linksys is old. Alternate driver for Sitecom WL-125 driver at [175] is newer version. With this, the card doesn't disconnect. Tested with card with usbid 1915:2234. 

---

### Post by cliff01 on 2007-03-18
My usbid is 1915:2234 and I tried the Sitecom driver and it was no better or worse than the islsm_usb I had blacklisted. I'm stunped. Ndiswrapper -l shows wusb54g as loaded and the hardware is present. Problem is iwcinfig or cwconfig (whatever it is) does not show anything but 'lo'.
What's my next step?
Thanks.

---

### Post by Floppyjoe on 2007-03-18
> **cliff01 said:**
> My usbid is 1915:2234 and I tried the Sitecom driver and it was no better or worse than the islsm_usb I had blacklisted. I'm stunped. Ndiswrapper -l shows wusb54g as loaded and the hardware is present. Problem is iwcinfig or cwconfig (whatever it is) does not show anything but 'lo'.
What's my next step?
Thanks.

Have you issued the commands:
```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by cliff01 on 2007-03-19
Thanks for the response.

I did these commands:
sudo depmod -a (there was no response)
sudo modprobe ndiswrapper
Then I got he following:
"Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument"

any ideas?

---

### Post by cliff01 on 2007-03-20
should I delete the file "ndiswrapper.ko" and try those commands again?

---

