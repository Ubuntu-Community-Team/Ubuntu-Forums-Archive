---
title: "Cannot get Epson Stylus TX550W network printer working"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by hfinger on 2014-04-18
[PARTIALLY SOLVED]

I have dumped Windows 7 at long last and have switched to Ubuntu 12.04.  My Epson Stylus TX550W wireless printer previously worked successfully on a WiFi lan and was successfully discovered and installed in Windows 7 Pro.

I have downloaded epson-inkjet-printer-stylus-tx550w-series_1.0.0-1lsb3.2_i386.deb and installed it with the Ubuntu Software Centre.  How to get this driver working and accessing the network Epson TX550W? Presumably by the Printing - localhost configuration dialogue, except  I cannot work out how to use it:


[LIST]
[*]Find Network Printer -- what or where is the host? 
[*]Internet Printing Protocol -- what URL should I type (example: ipp://cups-server/printers/printer-queue) 
[/LIST]

Can anyone help? I'm really stuck here.

---

### Post by hfinger on 2014-04-20
I found, downloaded and installed ...

epson-inkjet-printer-escpr_1.4.0-1lsb3.2_i386.deb
epson-inkjet-printer-stylus-tx550w-series_1.0.0-1lsb3.2_i386.deb
iscan_2.29.3-1~usb0.1.ltdl7_i386.deb
iscan-data_1.27.0-1_all.deb
iscan-network-nt_1.1.1-1_i386.deb

... from the Epson site (transferred from the previous Avasys repository). After rebooting Ubuntu 12.04.4, and choosing Gearwheel > Printers, the Epson Stylus TX550W was discovered. After another reboot, the Printer logo appeared on the taskbar, allowing access to the print queue. But it only sorta works. See separate post for slow printing issue.

---

