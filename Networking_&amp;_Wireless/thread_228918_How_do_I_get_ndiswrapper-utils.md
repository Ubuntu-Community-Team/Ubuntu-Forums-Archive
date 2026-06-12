---
title: "How do I get ndiswrapper-utils?"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by steveob on 2006-08-03
Just started using kubuntu on a Dell Inspiron 1300 and in common with many others!!! having problems with wifi.  Have tried to install ndiswrapper-utils with "sudo apt-get install ndiswrapper-utils" but get an error message "...has no installation candidate".

Have found ndiswrapper-utils on the live cd but the cdrom drive does not feature in the sources.list.  How do I include the cdrom drive in the sources list or get ndiswrapper-utils from the net?

Any help greatly appreciated.

---

### Post by ciscosurfer on 2006-08-03
Provided you're using Dapper and on an i386 machine, you can [go here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils_1.8-0ubuntu2_i386.deb&md5sum=15bf250f0a1114686655232175339cc2&arch=i386&type=main") to download (pick any mirror).  

Otherwise, [go here]("http://packages.ubuntu.com/") and select your platform, etc. and follow the links.

---

### Post by steveob on 2006-08-04
Many thanks ciscosurfer.  Followed your second link and found in Dapper list "ndisgtk".  Decided to install that first and lo and behold, it installed ndiswrapper-utils and all dependencies!  Just need to put the Broadcom Windows file somewhere now!!!

Thanks again, much appreciated.

---

### Post by ciscosurfer on 2006-08-04
Anytime, steveob!  Glad it helped!

---

