---
title: "O2 USB Modem with Hardy 64bit - is there a how to?"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by darkworld on 2008-10-02
Hi

Ive just got an O2 usb modem and I know it works with Ubuntu but Ive been told I need to find the how to... apparently theres a bit of work to do, unless things have changed? Can anybody point me? Found a few old threads on other sites but nothing complete for a novice. Can anybody help?

---

### Post by darkworld on 2008-10-02
ok heres how much progress I havent made!

> wvdialconf - scanning serial ports, finds nothing.

> rmmod usb-storage
rmmod usbserial
lsusb

finds usb printer and usb keyboard but not the usb modem, so no modem info. Some how to's for other usb modems suggest cancelling pin on sim but I havent currently got a phone for this sim. Would that prevent detection?

In Places > my compter > usb device shows and is mounted, properties, device unknown? any suggestions?

If this thread is in the wrong place could a mod move it to the correct forum. cheers

---

### Post by darkworld on 2008-10-03
please can someone tell me how i can find out the info from device so that i can set it up in network manager, ive checked the simm and pin lock is off.

wvdial doesnt find it, its says have you set serial correctly....what does this mean????

---

