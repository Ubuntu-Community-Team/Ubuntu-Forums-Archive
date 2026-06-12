---
title: "hello i've just been given a xerox scanner which isn't being recognised"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by hazeldwyer on 2010-01-04
i'veplugged it in and followed the instructions in help but itsnot coming up, any ideas would bemuch apreciated. thanks

---

### Post by halitech on 2010-01-04
which scanner and how is it connected?

---

### Post by lavinog on 2010-01-04
What instructions are you following?
What is the output of lsusb when you connect it?

---

### Post by hazeldwyer on 2010-01-05
hello,

its a xerox usb scanner, i followed the ubuntu help instructions which were to download the libsane-extras package then type alt+F2 and type in gksudo gedit /etc/sane.d/dll.conf then take the # from in front of the right driver bt i dont know which dreiver it would be, there wa axerox in the list but it didn't have a # in frontof it. the help said you may haveto install a driver or change some configuration?

---

### Post by Methuselah on 2010-01-05
> **hazeldwyer said:**
> hello,

its a xerox usb scanner, i followed the ubuntu help instructions which were to download the libsane-extras package then type alt+F2 and type in gksudo gedit /etc/sane.d/dll.conf then take the # from in front of the right driver bt i dont know which dreiver it would be, there wa axerox in the list but it didn't have a # in frontof it. the help said you may haveto install a driver or change some configuration?

Plugin in the scanner, wait a short while then type 
```

lsusb

```
in a terminal.

Post the output.
It is possible to determine scanner compatibility here:
[http://www.sane-project.org/sane-mfgs.html#Z-XEROX](http://www.sane-project.org/sane-mfgs.html#Z-XEROX)
but the precise device ID is needed.

Majority of Xeroxes seem to have poor support but you could get lucky.

---

### Post by hazeldwyer on 2010-01-05
Bus 002 Device 002: ID 0461:038b Primax Electronics, Ltd Xerox 2400 Onetouch
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Methuselah on 2010-01-05
This scanner is unsupported hardware...sorry.
[http://www.sane-project.org/unsupported/xerox-2400-onetouch.html](http://www.sane-project.org/unsupported/xerox-2400-onetouch.html)

I checked Xerox's website and they only have drivers for various versions of windows.
[http://www.xeroxscanners.com/en/uk/products/X2400/drivers.asp](http://www.xeroxscanners.com/en/uk/products/X2400/drivers.asp)

---

### Post by hazeldwyer on 2010-01-05
thank you very much for trying x

---

### Post by Methuselah on 2010-01-05
It is a real shot in the dark but you could try uncommenting 'genesys' backend in the sane conf file to see if it works in any way.

Don't expect much but they mentioned that it probably has similar hardware to other scanners supported by that backend so maybe you could give it a shot.

---

