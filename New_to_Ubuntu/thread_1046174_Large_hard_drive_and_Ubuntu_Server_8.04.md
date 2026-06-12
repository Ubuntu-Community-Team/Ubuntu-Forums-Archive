---
title: "Large hard drive and Ubuntu Server 8.04"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by rharring on 2009-01-21
I have an NTFS formatted, 1TB (1000GB) SATA hard-drive which I installed in an external case and connected it via a USB connection to my Ubuntu Server (a rather elderly Athlon 1100) on an Asus A7VL-VM motherboard.

I am unable to read the whole drive and am wondering if I am facing a problem with Ubuntu reading such a drive size or whether it is the BIOS on my motherboard. The motherboard Manual is quiet on the maximum  hard-drive size.

Going through /var/syslog shows this message:-

Jan 20 16:28:12 ubuntu-server kernel: [155200.020538] usb 1-2: new full speed USB device using uhci_hcd and address 3
Jan 20 16:28:12 ubuntu-server kernel: [155200.150439] usb 1-2: device descriptor read/64, error -71
Jan 20 16:28:12 ubuntu-server kernel: [155200.390270] usb 1-2: device descriptor read/64, error -71
Jan 20 16:28:13 ubuntu-server kernel: [155200.620117] usb 1-2: new full speed USB device using uhci_hcd and address 4
Jan 20 16:28:13 ubuntu-server kernel: [155200.750022] usb 1-2: device descriptor read/64, error -71
Jan 20 16:28:13 ubuntu-server kernel: [155200.989920] usb 1-2: device descriptor read/64, error -71
Jan 20 16:28:13 ubuntu-server kernel: [155201.219699] usb 1-2: new full speed USB device using uhci_hcd and address 5
Jan 20 16:28:14 ubuntu-server kernel: [155201.639418] usb 1-2: device not accepting address 5, error -71
Jan 20 16:28:14 ubuntu-server kernel: [155201.759328] usb 1-2: new full speed USB device using uhci_hcd and address 6
Jan 20 16:28:14 ubuntu-server kernel: [155202.179044] usb 1-2: device not accepting address 6, error -71

Any comments much appreciated.

---

### Post by logos34 on 2009-01-21
> **rharring said:**
> problem with Ubuntu reading such a drive size or...

+1.  (my guess at least)

look over at launchpad for bug reports

---

### Post by rharring on 2009-01-23
Hi logos34.

What does +1. mean?

When you say, "look over at launchpad for bug reports", does this mean that my problem has somehow been made a bug report? Sorry for dumb questions, I am having real difficulties understanding the philosophy of the whole site and the bug report function.

Regards

Roger

---

### Post by logos34 on 2009-01-23
> **rharring said:**
> Hi logos34.

What does +1. mean?

i.e. 'I agree', 'that's what I think too'

> When you say, "look over at launchpad for bug reports", does this mean that my problem has somehow been made a bug report? 

i.e. do a search of launchpad for possible bug reports--maybe there are some, maybe not, I haven't looked.

good luck

---

