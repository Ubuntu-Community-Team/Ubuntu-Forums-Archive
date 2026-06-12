---
title: "Unable to print from Qcad"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by rsgangr on 2009-11-18
I have just installed QCad (Version: 2.0.5.0 [Community Edition], Date: Sep 10 2007). To assist in understanding how it works I downloaded "QCad User Reference Manual, Copyright © 2006, Andrew Mustun" and "QCad Tutorial --- October 28, 2007 (David Dentlinger)".

QCAD is almost certainly adequate for my purpose (small design projects e.g. modifications to bathroom) but I have encountered a problem. I find that I am unable to send a drawing to my printer.

When I select "Print to printer" QCad does not see my printer. The only work-around seems to be "Print to file" that creates a Post-Script file. I can then open the file and print that but all colours on the drawing default to black.

I have no difficulty in printing from any other application, either from Ubuntu or Windows XP.

What am I missing here? Any suggestions are welcome.


Release: Ubuntu 8.04 LTS; Kernel 2.6.24-25-generic
Printer: HP Officejet 6213

---

### Post by doug1212 on 2009-11-18
Hi, there is a thread on the QCAD forum that may be of help with the printing issue.

[HTML]http://www.qcad.org/forum/viewtopic.php?t=356&highlight=printer&sid=f228ee46e8eb4d70c16ab152a931157a[/HTML]

Doug.

---

### Post by rsgangr on 2009-11-18
Doug1212:

Thank you for your quick answer and for directing me to the QCad forum. After reading through the posts there I was able to edit my "cupsd.conf" file to solve the problem.

Now QCad "sees" my printer and the plans are printed with the colours chosen on the various layers being correct - excellent!

---

