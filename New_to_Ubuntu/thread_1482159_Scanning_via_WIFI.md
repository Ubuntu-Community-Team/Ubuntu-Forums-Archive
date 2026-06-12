---
title: "Scanning via WIFI"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by pi24 on 2010-05-13
Hello! 

I'm trying the whole day to get our scanner (Ricoh Aficio 3025, it's a printer-fax-scanner multi) to work via WIFI with x-sane and simple-scan, but I did not manage.

They simply does not detect the scanner, however, I can easily print with it.

Do you have any experience in this?
Thanks in advance,
PI

---

### Post by pi24 on 2010-05-13
Oh I thought it's a simple issue to solve. :) The funniest is I can print via WIFI easily. For me, it'd be logical that this connection works backwards, too.

Another idea:
Supposing I could redirect the scanned data into a network folder, would I be able to access it from Ubuntu? I could simply try it out, but I'm off work.

Thanks in advance!

---

### Post by blazemore on 2010-05-13
The scanner is technically a seperate device.
The big plastic box that contains your printer, scanner (and fax?) has a USB hub that splits the one cable to the different devices. That one works is no indication that others are supported. 
Saying that, Ubuntu does support network scanning, although be aware that sending very large bitmapped scans over the netwrk, particularly over Wifi, may take a while

If you can, plug it in via a USB cable and see if it works. If it does, then the problem is with the network and outside the scope of my knowledge. If it doesn't work, proceed!


The first thing I'd do is install the "libsane-extras" package. This will make sure you've got all the scanner drivers, including those which aren't put on the CD by default.

You can click [here]("apt:libsane-extras") to install this package if you're in Firefox, or install it manually through the package manager.

It may be now that the scanner works. Try setting up the scanner from the Scanning utility again, and let us know if you run into any problems (or let us know if it works).

---

### Post by oldsoundguy on 2010-05-13
I may be wrong on this .. but since I first started using Linux, in the early days, that scanner had to be hard wired into the computer .. be it a stand alone, 3 way or 4 way unit.  Has to do with TWO WAY communications, and unless your scanner is one of the newer wireless units, think that is still the way things are.

---

### Post by pi24 on 2010-05-14
Guys, thank you for your advices! I will try to solve this issue but only on the next week. I'll let you know how it goes!

Thanks again,
PI

P.S. Yes I know scanning over WIFI is a stupid idea. The idea is not mine, I've told my boss that plugging it in directly would most probably solve the issue and it'd be faster, too. But this is what he wants. :-?

---

### Post by eltonw on 2010-05-14
> **pi24 said:**
> Hello! 

I'm trying the whole day to get our scanner (Ricoh Aficio 3025, it's a printer-fax-scanner multi) to work via WIFI with x-sane and simple-scan, but I did not manage.

They simply does not detect the scanner, however, I can easily print with it.

Do you have any experience in this?
Thanks in advance,
PI

A couple of suggestions:

1) You would be better off posting this in the **Networking** section.
2) Linux does not grant access freely, and thus you need to give 'permissions' to access the device: scanner, printer, whatever peripheral that is connected to and is* visible* on the network. 

A search on 'wireless devices' or _google for "wireless device compatibility configuration linux"_ should bring you answers and solutions.


HTH...

---

