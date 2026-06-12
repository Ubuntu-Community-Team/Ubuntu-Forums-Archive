---
title: "Printer Installation..."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by all4him on 2008-12-07
Hello folks,  I am still wet behind the ears, as for Ubuntu goes. I have been trying all weekend to get my Brother printer<MFC210C> working.  I have gone to the Brother website, search for drivers and even downloaded the drivers<lpr/cups>. But, still cannot get it going.. It says the printer is idle/ready, I go to print and it says 'error in printing'..

Someone please help an inspiring Ubuntu user!! :confused:

Thanks for your help,


all4him

---

### Post by halitech on 2008-12-07
only thing I found was this thread

[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

---

### Post by plucky on 2008-12-08
If you are using 8.04 or 8.10,use **Synaptic Package Manager** to install the drivers.

Open Synaptic and search for MFC-210c and it should show you the Cupswrapper and LPR drivers.Install both.

Power on and connect printer.

Then open **System > Administration > Printing** and select New Printer.
It should then search and find your printer and then search for drivers to install.Select one and install.Then do a test print.


Good Luck

For scanner installation,use the Brother Website or this [thread](http://ubuntuforums.org/showthread.php?t=590793)

---

### Post by Peter09 on 2008-12-08
Try opening a browser window and typing in the address

[http://localhost:631](http://localhost:631)

This should give you the Cups Printer Interface

---

