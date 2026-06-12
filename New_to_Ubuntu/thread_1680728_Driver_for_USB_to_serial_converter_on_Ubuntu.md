---
title: "Driver for USB to serial converter on Ubuntu"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by neel148 on 2011-02-03
I am using the Bafo BF-810, a usb to RS232 converter. I called up the local distributor who told me that a driver which supports ubuntu or for that matter linux doesn't exist. Has anyone else worked on it. If yes then what is the solution to the problem. Does some other converter also exits that supports Ubuntu?

---

### Post by HermanAB on 2011-02-03
In my experience, the Belkin USB Serial adaptor 'Just Works'.

---

### Post by sandugandhi on 2011-07-05
> **neel148 said:**
> I am using the Bafo BF-810, a usb to RS232 converter. I called up the local distributor who told me that a driver which supports ubuntu or for that matter linux doesn't exist. Has anyone else worked on it. If yes then what is the solution to the problem. Does some other converter also exits that supports Ubuntu?

I also bought BAFO BF-810 and loaded the modules usbserial pl2303 
But, stiil, the BAFO is not detected. On dmesg, I get

unable to enumerate usb device on port 2

Btw, my usb port works.
I got another serial to usb cable from Trendnet TU-S9 (costly, but works out of box.) Ubuntu (Natty) simply loads the above drivers in correct order and dmesg gives correct output
that serial usb mounted on ttyUSB0
Also, lsusb gives Prolific 2303 with correct Vendor id device id.

   What is the problem with BAFO, I am not able to figure out.

---

