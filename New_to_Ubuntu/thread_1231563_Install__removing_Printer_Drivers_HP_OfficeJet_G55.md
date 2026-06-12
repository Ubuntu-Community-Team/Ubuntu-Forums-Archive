---
title: "Install / removing Printer Drivers HP OfficeJet G55"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Neill_R on 2009-08-04
Install / removing Printer Drivers HP OfficeJet G55

Hi
 
 I am new to Linux and have Xubuntu 9.04 installed and mostly running well. However I determined WRONGLY i believe that there was a better (newer) driver for my printer. However I am not sure my operating system is supported. While the printer once attached by USB cable worked straight-away. The install of hplib3.9.6b has installed another printer but not removed the old printer although I think the software has gone.
 
 The result is I wish to some how return to as it was. I am assuming one removes the new driver and then reinstalls the one as supplied with the orginal CD/Update the verion of that was 3.9.2. How to help please.

Neill

---

### Post by Neill_R on 2009-08-05
Can any guide me to how to remove the package I installed

---

### Post by Sef on 2009-08-05
How did you install it?

---

### Post by Neill_R on 2009-08-05
Download and Following instruction see 

[http://hplipopensource.com/hplip-web/models/officejet/officejet_g55.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_g55.html)

---

### Post by Bucky Ball on 2009-08-05
HPLip should have detected any printers that were plugged in when you get to the part in the installation where it ask you to choose one of about four options. One is unplug and re-plug the printer. That should have been the only printer it installed.

At the end, from memory, it asks if you would like to install another device or you can do that from the hp-config in the drop down menus. This GUI would also allow you to remove any printers that no longer physically exist.

Is the driver actually running the printer okay? I found the new driver finally got my mother-in-law's CP1215 installed, but that model doesn't work 'out of the box' (needs separate plug-in).

---

