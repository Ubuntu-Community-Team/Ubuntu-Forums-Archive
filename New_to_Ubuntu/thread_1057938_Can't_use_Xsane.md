---
title: "Can't use Xsane"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by gabo.cr on 2009-02-02
Hola

I have a Visioneer Onetouch 8920 scanner.
It seems is [not supported]("http://www.sane-project.org/cgi-bin/driver.pl?manu=primax+electronics&model=visioneer+onetouch+8920&bus=usb&v=0461&p=0371") by Xsane.

Is there any other scanner program out there that doesn't use Sane's library?

I'm getting this in terminal:

**lsusb**
Bus 003 Device 003: ID 0461:0371 Primax Electronics, Ltd Visioneer Onetouch 8920 Scanner

**sane-find-scanner**
found USB scanner (vendor=0x0461, product=0x0371) at libusb:003:003

I have rights to use the scanner under "groups".
Any help will be appreciated.
:(

---

### Post by khelben1979 on 2009-02-02
From what I have read on different places on the net, your scanner don't work with Linux. I think you're out of luck on this one.

---

### Post by Idaho Dan on 2009-02-02
gabo.cr,
same problem with my Visioneer 9450.
Not on the xsane supported list.
I have to use my HP scanner.

---

### Post by gabo.cr on 2009-02-02
Alright, I guess I can't use it.
I have a dual boot with Vista and Ubuntu.
There are no drivers for Vista either !!
This is not my day.

[-X

---

### Post by desertdog on 2009-03-04
Idaho Dan-.
You might want to check out the VueScan software at [http://www.hamrick.com/index.html](http://www.hamrick.com/index.html). They claim to support the Visioneer 9450. It is not open source and will cost you some money.

Also check out [http://www.exactcode.de/site/open_source/saneavision/](http://www.exactcode.de/site/open_source/saneavision/). Your scanner appears to be supported by the sane avision backend.

---

