---
title: "Windows XP Printer sharing."
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by dgonza9 on 2008-07-17
I'm pretty new.

Quick question.  I have a printer that is considered a linux "Paperweight" by linuxprinting.org.  I'm wondering if I can install the printer on my windows box, then print from my linux box to it as a shared network printer.

I've tried a few things and it's not working out, so I figured I'd better check to see if it's possible.

Thanks.

---

### Post by dgonza9 on 2008-07-17
Anyone?  I'd really appreciate it.

---

### Post by itendo on 2008-07-21
I'd like to give you advice, but I can only offer condolences and found your post because i am having a similar problem. the issue is sharing a printer in XP and Hardy Heron.

I have a dual boot desktop (HH/XP), an HH laptop, and an XP laptop. I have been able to successfully get file sharing string across all three, no matter the dual boot's loaded OS. 

The printer (HP PSC 1315) is attached to the desktop. The bulk of use is from the XP laptop, both in scanning and printing; it works fine. The desktop can has it installed and functional for either OS boot. The problem is with the HH laptop; it has "installed" the printer successfully, but when i try to print, what happens is a) print mngr in XP shows the print job, b)it spools the entire doc, & c) the paper jerks like its going to feed and print, but thats where it stalls out.

i dont know if maybe i need to boot the desktop in HH for it to spool it all the way, or install some MS-Imaging linux operative, or whatever.

for those out there having issues with the drivers and installing the printer to begin with, heres two resources:

[http://hplip.sourceforge.net/supported_devices/index.html](http://hplip.sourceforge.net/supported_devices/index.html)
((this is a search engine to see what HP models are compatible and how with linux))

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00302767&lc=en&cc=uk&dlc=en&softwareitem=dj-7294-5&product=90787&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00302767&lc=en&cc=uk&dlc=en&softwareitem=dj-7294-5&product=90787&os=228&lang=en)
((this is a table of alternate drivers that can be substituted if the particular model is not installing on your box))

---

### Post by dmizer on 2008-07-21
you must have a driver for the printer in order to print to it.  this goes for a printer connected directly to your computer, as well as a computer shared over a network.

so, if there is no good driver for your printer when directly connected, your situation will be no different when shared across your network.  and, if linuxprinting.org labels your printer as "paperweight", it would seem that you're basically out of luck.

---

