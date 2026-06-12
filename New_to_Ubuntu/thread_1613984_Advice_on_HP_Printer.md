---
title: "Advice on HP Printer"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by lyni on 2010-11-05
I've always had an HP Printer and now I need to buy a new one because this one is breaking down. I want another HP Printer because this one has worked well with my Ubuntu system.
I've been looking at a HP Deskjet F4480 and a HP Deskjet 2050. both of them say they are compatible with microsoft only. there's no mention of Linux systems.

does anyone know if these will work on my Ubuntu 10.4?

thanks
lyn

---

### Post by ibizatunes on 2010-11-05
HP printer have VERY good support, just have a quick google..... HP are properly the best printer for linux support out of the box

---

### Post by TNT1 on 2010-11-05
Both are listed here:
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
you should be fine.

---

### Post by lyni on 2010-11-05
> **TNT1 said:**
> Both are listed here:
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
you should be fine.

thank you TNT1.
I will bookmark that site.
it told me that the HP Deskjet F4480 is supported but the HP Deskjet 2050 is not supported but I can download their program to make it compatible.

that site gives me some good information.
thank you again for taking the time to reply to my query.
lyn

---

### Post by sleepingdragon on 2010-12-16
*** UPDATE 2 *** The new drivers from hplipopensource (3.11.x) now detect  the scanner, and seem to be available in the repos for Ubuntu 11.04. You  can install their new drivers via their instructions to get the 3.11.x  working in 10.10, and I would suspect 10.04 works too. XSane seems to do everything it should do and the scanning results look fine.

Sadly, the 2050 is still not supported for scanning. I've tried the installing the .run file from hplipopensource, I have also compiled their source code, but all for nothing. The scanner is simply *not there*.  This issue is far from SOLVED.

Printing is great though, absolutely no problems with ink quality.

*** UPDATE *** Oddly, sane-find-scanner finds the scanner at the right USB port with no problems, but this isn't being passed onto *xsane, simple-scan* or *scanimage*. Ideas anyone?

dracnoc@maverick:~$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
[B]
found USB scanner (vendor=0x03f0 [HP], product=0x8711 [Deskjet 2050 J510 series]) at libusb:001:009[/B]
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

