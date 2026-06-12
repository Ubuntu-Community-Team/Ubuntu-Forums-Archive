---
title: "Epson NX420 scanner"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by kingofspades8 on 2011-06-14
I recently bought an Epson Printer/Scanner all in one, the model is NX420.

The printer prints just fine on Ubuntu 11.04 64 bit using the printer driver package 1.0.3-1lsb3.2 (epson-inkjet-printer-escpr). However, it won't scan.

I've tried the following in the command prompt, with the following output:

sane-find-scanner: 
found USB scanner (vendor=0x04b8, product=0x0864) at libusb:001:006

Note: the vendor and product number above are correct for the model.

scanimage -L:
No scanners were identified. If you were expecting something different, check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool (if appropriate).

Both Xsane and SimpleScan don't find any scanners.  I tried contacting Epson and they told me they don't support Linux drivers and neither does Avasys.  

Any ideas on how to make this work?

---

### Post by kingofspades8 on 2011-06-15
After a bit of digging around I found this:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo)

Installing the packages has to be done one by one in the following order:

iscan-data, then iscan-core

Problem solved!  :popcorn:

---

