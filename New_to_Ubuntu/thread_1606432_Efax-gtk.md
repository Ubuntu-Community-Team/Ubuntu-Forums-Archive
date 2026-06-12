---
title: "Efax-gtk"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by jackwilson on 2010-10-26
When I send a fax I get this error message  GPL Ghostscript 8.71: Unrecoverable error, exit code 1 Not valid postscript file.
what do I need to do to fix, and how do I fix it so I don't get this error message?

---

### Post by nicholse on 2010-11-05
efax-gtk-3.0.17

I am having the same difficulty and am including more information.

I make a text file, save it as test.txt and use

#efax -ntest.%03d test.txt
efix: Fri Nov  5 00:19:01 2010 efix v 0.3 Copyright 1999 Ed Casas

this creates test.001 as a tiff
when I use efax-gtk to send that I get the error:

GPL Ghostscript 8.71: Unrecoverable error, exit code 1
Not valid postscript file

If I use gedit to print to file postscript and try and send that I get the error:

efax-0.9a: 00:23:20 Error: can't read multi-strip TIFF files
efax-0.9a: 00:23:20 Error: missing offset to TIFF data
efax-0.9a: 00:23:20 finished - unrecoverable error

# cat /proc/version
Linux version 2.6.32-25-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010

Trying to open test.001 in Eye of GNOME 2.3.0 gives a blank page.

If I use gs to create the tiff I get a good looking tiff but efax-gtk still errors with :
GPL Ghostscript 8.71: Unrecoverable error, exit code 1
Not valid postscript file

gs -q -sDEVICE=tiffg3 -dNOPAUSE -sOutputFile=test.using-gs-ps-to-tif.%03d test.ps </dev/null


The attached zip file contains test.txt, test.001 (tiff), test.using-gs-ps-to-tif.001 and test.ps

looks like there may be an issues with efax in creating valid tiffs?

Maybe a moderator will move this to an efax or gs forum?

Eric

---

### Post by RogerDavis on 2011-06-23
I get the same error message   "GPL Ghostscript 8.71: Unrecoverable error, exit code 1
Not valid postscript file"   when trying to send a fax (.jpg, .rtf, .odt  pretty much anything except a .pdf).

When attempting to send a .pdf  I get  "efax-0.9a: 13:13:22 Error: can't read multi-strip TIFF files
efax-0.9a: 13:13:22 Error: missing offset to TIFF data
efax-0.9a: 13:13:22 finished - unrecoverable error"

Is this a modem setting problem, a hardware problem, or an eFax problem?

---

### Post by jtarin on 2011-06-23
Not too difficult.....found this. A little dated but applicable and logical.

> GPL Ghostscript 8.71: Unrecoverable error, exit code 1
**_Not valid postscript file_**

> eFax is telling you to use a postscript file, so a pdf, txt, etc. won't work. Fortunately, it's easy to convert documents to postscript format using Open Office Word (OO). To do so, you need a postscript printer driver, though you don't have to have a postscript printer.

To install the postscript printer driver in Ubuntu, click System -> Administration -> Printing, then double-click 'New Printer'. Ubuntu will search the printer database and look for installed printers. If you don't have a printer connected, it will take a while, but be patient and soon you will see the 'Add a Printer' Dialog. Select 'local printer' and 'use another printer by specifying a port', then click Forward. Choose Apple as the manufacturer, and pick one of the Laserwriter printers, which conveniently use an already-installed postscript printer driver. Click Forward, and finish the install with whatever name you want for the printer.

When you start OO again (restart it if it was open when you added the printer), you will have your newly installed printer as an option in the File -> Print Dialog. Open the document you wish to fax, choose File -> Print. Select the Apple Laserwriter you installed and check the 'Print to file' box. When you click 'Print' the file will be saved to the current directory with a '.ps' extension.

Back in eFax, select the postscript file you just created and you should be able to fax it.

There is also a way to fax using eFax directly from OO, but I haven't got that set up. Yet...

---

### Post by RogerDavis on 2011-06-23
Interesting - I was confused with a .pdf.  

Is there some real reason that it won't send other files, like .txt or .jpg, or ???

---

### Post by jtarin on 2011-06-23
[Some Post Script enlightenment]("http://merganser.math.gvsu.edu/david/psseminar/index.html#render"). Think of it as a Fax Machine without all the plastic, paper and mechanics.
More links at bottom of linked page.

---

### Post by RogerDavis on 2011-06-24
I get the picture - it relies on postscript to make the vectors that Windoze fax programs do internally?

Anyway, next question - will efax work with a WinModem?

Thanks!

---

### Post by jtarin on 2011-06-24
I used to use an external Zoom modem for fax and it works great under Linux. Winmodems.....maybe but you'll have to research.[Here's a start.]("http://www.faqs.org/docs/Linux-HOWTO/Winmodems-and-Linux-HOWTO.html")

---

