---
title: "usb-internet"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by eier on 2007-11-02
Hi.

I got a usb-internet modem on my computer, and i can't get it to work under ubuntu.
When i plug it in on my m$VISTA it installs itself, so i rebooted and ran the program trough wine,but it says that it can't find the usb-modem. Is there any way i can emulate trough wine?
Hate being stuck with vista, and acer's bloatware.
here's a picture of the [usb-device]("http://images.gfx.no/322/322710/modem.jpg")
I emailed the company that makes it and they say they don't plan making drivers for Linux, but they have drivers for Windows and macOSX.

Any help will be appreciated.

---

### Post by grEnAlEins on 2007-11-02
You can use ndiswrapper in conjunction with the XP driver to make it work in theory.  I never had luck with ndiswrapper though.  You could also check to see if you can use the BCM43xx driver and try it that way.  I do not know enough about the device you have to tell you which though.  Sorry.  I am sure somebody knows exactly what you could do.

---

### Post by eier on 2007-11-09
Thanks for replying.

The usb device is not a wireless card, it is a antenna that connects to the internet trough GSM or 3G.
It has it's own sim-card too, i have to type my pin code to connect to it.
So i doubt the wireless driver's will work...

---

