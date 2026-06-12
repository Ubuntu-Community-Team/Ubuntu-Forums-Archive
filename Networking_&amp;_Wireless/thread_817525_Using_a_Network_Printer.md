---
title: "Using a Network Printer"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Nitewalker on 2008-06-03
I am trying to use a printer that is attached to another computer that is also running Ubuntu 8.04 thru my wireless network.  The address of my laptop is 192.168.0.100 and the tower computer with the printer on it is 192.168.0.101.  I can ping both addresses from either machine and can get onto the Internet.  Printer on tower is marked as shared and is using cups.  What do I need to do:confused:

---

### Post by chili555 on 2008-06-03
The hard way: BIND, samba, netbios and probably a lot more.

The easy way: use a static IP address on your static machine, the tower. Then on the laptop, go to System -> Administration -> Printing and add a new printer. Since it will not see a printer attached to the laptop, a network printer will be assumed. I use the ipp protocol. The host will be ipp://192.168.0.101:631. Port 631 is the port cups uses. The queue will be /printers/<name of your printer>

I suggest going over to the tower to verify what the printer is actually named there, for example, Epson or Samsung or ML-2010 or whatever. What pops up in the print dialog when you print from the tower?> Print to file
ML-2010
PDFThe queue will then be /printers/ML-2010 for example.

Click OK and the laptop will see if it sees the printer out there in the network, install a driver and after all this is accepted, you should test by printing a test page. If all goes well, you will get a page.

---

### Post by Nitewalker on 2008-06-03
Thanks for the info----I had made some changes to my etc/hosts file and correcting some host name errors and all of a sudden the printer appeared on the network, I was just on my way upstairs to the tower to do what you were talking about with my laptop when I noticed that the printer was there as soon as I went to 'system---printers'....thanks again for you help:popcorn:

---

