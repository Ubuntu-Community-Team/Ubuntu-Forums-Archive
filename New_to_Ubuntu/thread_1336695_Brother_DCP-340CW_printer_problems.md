---
title: "Brother DCP-340CW printer problems"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by sparky-trev on 2009-11-24
Hello
I installed 9.10 Karmic Last week all well except the printer
If you go system>admin>Printing
devices shows the printer connected to a USB port.
printer configuration-local host shows the correct printer with a warning ! triangle
following the Help tab finally comes up with brlpdwrapperMFC210C driver missing not installed. 
I have tried to follow marcw's  method at
 [http://ubuntuforums.org/showthread.php?t=71104&highlight=scanner](http://ubuntuforums.org/showthread.php?t=71104&highlight=scanner)
installed

Cups
Xsane
sane 
csh

visited the brother site to get the drivers LPR installs fine automatically with GDebi 
However the the Cupswrapper fails.

I have been trying a few things in the terminal and other things from book/mags etc but no joy!
 My machine has a cheap PC Chips MO using an AMD 2800 mobile processor it came bundled with won't work with the Athlon 64 it's suppose to work with, Google shows this is a common occurance.
Any help greatly appreciated.......... Trev

---

### Post by mikewhatever on 2009-11-25
If you want help with the driver that fails installing, do post an error message. That out of the way, both lpr and cups-wrapper for MFC210C are in the repositories. Just install brother-lpr-drivers-extra package.

---

### Post by walt.smith1960 on 2009-11-25
Did you check for "before installation" section of Brother's web site? Mine were on the same page as the drivers.  I installed two MFC Brother machines. In each case there were a few lines to be input in terminal before installing the .deb package. I found the directions more complex than needed but I printed them out and crossed out the sections that don't apply to my printer(s). I've had good luck with Brother printers under Ubuntu.

---

