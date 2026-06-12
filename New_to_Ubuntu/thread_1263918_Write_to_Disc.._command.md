---
title: "Write to Disc.. command"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-09-11
Anyone know the command that will bring up the window on a ISO image, just like when you right click on a ISO image, it will give you a option to Write to Disc.. below.

I kind of want that same window but to be able to do it through a command line, if it is possible, thanks in advance.

---

### Post by Hospadar on 2009-09-11
[http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)
here's something I found on google, looks pretty straightforward.  There are other ways to do it, there are several tools to burn from the command line (and in fact most graphical tools are merely frontends to aforementioned tools).

---

### Post by ericeclifford on 2009-09-11
This is what I get when I try to burn a ISO image to a blank DVD, 

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.


AND REPEATED THIS 

Unable to open this SCSI ID. Trying to map to old ATA syntax.This workaround will disappear in the near future. Fix your configuration.







I wish I could find the command to tell a pop up to come up, just like the GUI one of Write To Disc..

---

### Post by ericeclifford on 2009-09-11
Ahh I changed my device to /dev/scd1 and it seem to do something, but I have 2 dvd drives, and I am trying to write a script so it is in the live cd envrionment. I wonder if /dev/scd1 is the default for empty device or accessible device no matter which drive I have the live cd in?

---

### Post by cariboo on 2009-09-11
If you don't mind an Ncurses interface try mybashburn, it is in the repositories

---

