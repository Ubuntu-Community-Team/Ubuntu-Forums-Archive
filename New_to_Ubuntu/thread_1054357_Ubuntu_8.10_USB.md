---
title: "Ubuntu 8.10 USB"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by JPtux on 2009-01-29
I'm wondering if it is possible to have different video drivers for different computers on my ubuntu 8.10 4gb usb. Would it mess up anything? What do I have to do?

---

### Post by ByteJuggler on 2009-01-29
Well, the move in the X Windows server (Xorg) that Ubuntu uses is towards auto-detection.  This means in an ideal world it will automatically run on any supported hardware for which you install the driver package.  That is however a work in progress so isn't perfect yet.  Nevertheless, what you want should mostly work, on well supported hardware.  (Consider that the LiveCD faces the same challenge and gets away with it mostly.)  All you should need to do is ensure that you have all needed drivers installed.  Having them installed wont hurt anything.

---

### Post by JPtux on 2009-01-29
What if I happen to install a driver on my usb for a 6150 LE onboard Nvidia, then I use the ubuntu usb on another computer with a different card. Would it work or would I be able to download a driver for the second card?

---

### Post by JPtux on 2009-01-29
I guess I'm just going to have to try it out my self.

---

### Post by ByteJuggler on 2009-01-29
> **JPtux said:**
> What if I happen to install a driver on my usb for a 6150 LE onboard Nvidia, then I use the ubuntu usb on another computer with a different card. Would it work or would I be able to download a driver for the second card?

Just install both driver packages. I think by default most drivers are instsalled anyway.  So it should just work (TM).

---

