---
title: "DP-301P+ Print Server &amp; Gutsy"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by mgaskell on 2007-10-29
I cannot find/install my network printer in Gutsy. The server is attached to the parallel port of my HP Laserjet printer. It worked before. I have logged onto the server and obtained the following settings:

Server Nave:  PS-DD787A
Model:           DP-301P+
MAC Address: 00 15 E9 DD 78 7A
IP Address:    192.168.1.110
Printer Name/Port Name : PS-DD787A-P1

I've tried Jetdirect. I've tried SAMBA. I've inserted all combination of settings that I can think of. I cannot print a test page.

Can anybody help me set up this print server?

Thanks

---

### Post by mgaskell on 2007-10-29
I know that I can communicate with the printer because I can print a test page from the server set up screen in my browser. I just cannot print a test page from the Gutsy new printer install page.

Man, I'd hate to go back to Windows.

---

### Post by maxbur on 2007-11-01
LAN detection did not find my laserjet 1100 (attached to a print server on an ethernet router),  but a manual setup through the CUPS web interface worked. Try this:

Open CUPS in your web browser ([http://localhost:631](http://localhost:631))
Choose "Add Printer" and fill info boxes on the first screen.
After continuing to the second setup screen, choose "LPD/LPR Host or Printer"
On the following screen enter "lpd://192.168.xxx.xxx/LPT1" - use your own print server IP address; if necessary replace "LPT1" with the print server queue name suggested by the manufacturer of your router. (You might also check the router manual to ensure that it supports Unix printing.)
The following setup screens will recommend and setup the necessary drivers.

The Ubuntu printer setup utility could also be used, but whichever you choose, stick with it to avoid conflicts between competing software packages.

Although my printer works, I have yet to solve the annoyance of an extra blank page at the end of every print job -- an apparent bug which I'm still researching. (Could be [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155826](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155826), or one of several other possibilities.)

---

