---
title: "CUPS: One printer works another doesn't"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by mbirth on 2008-08-19
I'm just trying to setup a Win2k image in VirtualBox to use STAMPIT (a program to print stamps) with my LabelWriter.

The LabelWriter is named "LabelWriter320" in CUPS and is connected to using USB. There's another printer connected via LPP and named "hl1030".

Using the Win2k (all with latest updates) I can add the "hl1030" using the URL [http://192.168.0.235:631/printers/hl1030](http://192.168.0.235:631/printers/hl1030) - as expected. But trying to add [http://192.168.0.235:631/printers/LabelWriter320](http://192.168.0.235:631/printers/LabelWriter320) gives a

> Connect to Printer
Could not connect to the printer. You either entered a printer name that was incorrect or the specified printer is no longer connected to the server. Click Help for more information.

Opening that URL with the MSIE shows the CUPS configuration page for the LabelWriter.

All sharing settings should be correct.

Anyone got any hint?


Cheers,
  -mARKUS

---

