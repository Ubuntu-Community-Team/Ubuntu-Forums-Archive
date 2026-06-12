---
title: "network printer found and identified, but won't print"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by mrdavidberry on 2010-10-19
I am using ubuntu 10.10 and today took delivery of a Kyocera-Mita FS-1010 printer.

I plugged the printer into my router and did the 'add printer' thing asking it to find a network printer.  Hurrah! I thought, it has found the printer on the network, happy days.  I downloaded the appropriate ppd file and tried to print the test page.

'The printer may be unplugged or turned off' except that nothing has changed since ubuntu found it in the first place.  

I've tried it via usb and it was fine, except I want it networked!

Help!

---

### Post by wojox on 2010-10-19
As had similar problems with a Brother Printer. Delete the found printer and try searching the network again. Also try logging into your router to see if it recognizes it.

---

### Post by mrdavidberry on 2010-10-20
Fixed!

Printed the status page, it showed an IP address of 10.38.67.75 and DHCP as off.  The network card on my FS-1010 is an IB-21e.  I found some instructions to factory reset it [here]("http://ftp.kmu.edu.tw/Win/driver/printer/Kyocera/FS-6750/NETWORK/IB20/Docs/English/UserMan-21E/troubleshoot.htm").  After the the DHCP worked and the test page printed.

Yay!

---

