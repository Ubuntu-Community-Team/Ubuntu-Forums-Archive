---
title: "Printer connected via USB to Belkin Router"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by kiranvinayan on 2014-01-05
I have a Belkin N600DB router. I have connected a printer(HP Laserjet 1018) to the router via USB. What should be done to print from my laptop which is running 12.04 ?

---

### Post by tomearp on 2014-01-05
I don't envisage this being possible. The [user manual]("http://www.belkin.com/networking/manual/MAN_F9K1102_8820-00777_RevA03_N600.pdf") describes the process for Windows and Mac users; you need to install the Belkin Router Manager (which happens when you set the device up using the supplied CD) and that will allow the USB device to be mapped across the network to the computer. The router does not make any attached USB device directly network-accessible.

The system requirements list Windows and Mac only as the compatible operating systems for their router management software.

---

### Post by tomearp on 2014-01-05
[Something like this]("http://www.linux-hardware-guide.com/2013-05-01-tp-link-tl-wps510u-printserver-wifi-usb") will serve up a USB printer as a network-accessible device that can then be connected to with [CUPS]("http://www.cups.org").

---

