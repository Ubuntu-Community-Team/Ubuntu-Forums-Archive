---
title: "Logitech wireless keyboard/mouse not working 10.10 ubuntu"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Artone on 2011-06-28
Wireless keyboard is not working, I am having nothing but trouble. Wireless mouse will not work either. Can't pass "gnu grub version"
Strongly considering switching to windows. Everything seemed better and simple to use. Ubuntu is proving to be a huge pita for the novice. 
Thanks for advice.

---

### Post by jtarin on 2011-06-28
Give model number of keyboard and mouse.Try not to post two threads on similar issues......it's not helpful.

---

### Post by Artone on 2011-06-28
Sorry about that.

Logitech keyboard mod# Y-RK56
Logitech mouse mod# M-RR95

---

### Post by jtarin on 2011-06-28
[Go here]("http://www.hidpoint.com/hidpoint/download.html") and download HID for your mouse and keyboard and version of Ubuntu.
[Uninstall and Installation instructions.]("http://www.hidpoint.com/hidpoint/support/installing-hidpoint.html")

---

### Post by josephmills on 2011-06-28
along with what jtarin said could you pug them in and then open your terminal (ctrl+alt+t) and enter in ```
lsusb
``` then paste that here.

---

### Post by Joherrer on 2011-07-02
I  had a similar issue when changed to 11.04.
Unity didn't acknowledge my wireless mouse-keyboard combo.
So I'm using classic. 
My combo is Genius SlimStar i820.
jorge@jorge-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2628 Pixart Imaging, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer
Bus 003 Device 006: ID 0458:00ae KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 005: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 048d:8903 Integrated Technology Express, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Thanks for your help...

---

### Post by Artone on 2011-07-04
Did everything I was supposed to, now mouse works but keyboard seems to be dead. New batts, nothing. Any advice? New keyboard will work, or does it sound like an external problem? Thanks.

---

### Post by jtarin on 2011-07-04
> **Joherrer said:**
> I  had a similar issue when changed to 11.04.
Unity didn't acknowledge my wireless mouse-keyboard combo.
So I'm using classic. 
Did follow this advice?

---

### Post by Artone on 2011-07-04
Yes. Actually had a techie classmate to do it, and we tried keyboard on a laptop nothing, but mouse operates.

---

