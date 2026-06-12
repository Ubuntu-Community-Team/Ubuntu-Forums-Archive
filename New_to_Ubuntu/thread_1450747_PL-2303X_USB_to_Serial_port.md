---
title: "PL-2303X USB to Serial port"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by madaptive on 2010-04-09
I am using ubutu versio 9.04 and am trying to talk to the new pl-2303x usb to serial port and am not being able. From searching the web I see that earlier versions of ubuntu had problem detecting the pl-2303 usb-serial port due to inability to differentiate between pl-2303 and pl2303x (bMaxPacketSize0        64). I wanted to find out if anyone has had success in using the pl-2303x with ubuntu 9.04. If so what exactly did you do.

thanks!

---

### Post by madaptive on 2010-04-09
wondering if I need to install any drivers ... ?

---

### Post by madaptive on 2010-04-09
I found the solution at the below link:

[http://forums.reprap.org/read.php?12,4546](http://forums.reprap.org/read.php?12,4546)

Thanks.

---

### Post by scigghia on 2010-04-17
Hi, I am also in trouble with the device pl2303x
I tested it on Hardy and Karmic, but does not work!

I tried your solution but nothing!

someone could help me?

---

### Post by jsbu on 2011-01-17
Under Ubuntu 10.10 both pl2303 and pl2303x USB-serial cables worked with minicom 2.4 using the stock driver AFTER I ensured hardware flow control was turned off in minicom.

---

### Post by kf7nnz on 2011-01-25
> **jsbu said:**
> Under Ubuntu 10.10 both pl2303 and pl2303x USB-serial cables worked with minicom 2.4 using the stock driver AFTER I ensured hardware flow control was turned off in minicom.

Totally new to Ubuntu (v.10.10) here. Under Windows, the 2303 would redirect COM3 to the USB port. Under Ubuntu, it does not appear to automatically redirect a serial port (/dev/ttySn). This is a problem because the software I'm using expects the hardware to be on a serial port, not a USB port. How do you overcome this?

---

