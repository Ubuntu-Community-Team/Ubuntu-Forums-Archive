---
title: "Airlink101 printer server ok Windows/linux/Mac"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by stjohnh on 2008-06-05
Probably like a lot of you, I have a home with lots of computers running different operating systems. After a bunch of hours fiddling around I now have the AirLink101 AMPS240W (FRY'S) Wireless printer server connected and working on all. Now I don't have to leave my desktop unit on all the time so others can print !!!
Details of units:
AirLink 101 Wireless AMPS240W printer server- $30-40 ($20 on sale) at Frys. Also on Frys.com
Router is also AirLink101, but that is nothing special.
Network originally set up under windows XP, but now there are usually no windows boxes connected.
Desktop runs Mint 4 (a modified Ubuntu)(dual boot, I have one program that requires WinXP)
Also on network is a MacBook running Leopard OS X, Asus EEEPC running Xandros Linux, Old GQ laptop running mint with plug in USB wireless.
ALL these are printing to the Print Server !!!! Printer is a cheap Samsung ML-2510.

Hints to get all this running:
Install the provided configuration software for the printer server on a windows machine and configure the printer server via temporary ethernet connection to router (this is the only part that requires Windows, and only for a one time setup). Be sure to pick a static IP address (or else if you have a power failure or unplug something the IP address of the printer server will change and you can't print).

Look on the Printer Server configuration screen to get the IP address of the Printer server (mine is 192.168.1.113 yours will be very close)  and note the "printer" name (mine is PS-0AF49B-U1, yours will probably be the same if you use this printer server).

To configure printing on the computers running different operating systems use the add printers function, pick network printer, then UNIX or LPD type (IMPORTANT). For Host name, put in the IP address (i.e.  192.168.1.113  no http, no ipp, no slashes). Some systems ask for a Queue, put in the "printer" name (i.e. PS-0AF49B-U1). Remember that the computer sees the Printer Server as some kind of unknown usb printer. After putting in the address info for the printer server you will be asked to pick a driver, put in your real printer name and model (mine is Samsung ML2510, Mint Linux doesn't list that one but the ML-1510 driver works fine). Windows machines may ask for the disk that came with the printer. The Mac setup required that I install the Mac driver from the disk that came with the printer. 

The quick start guide that comes with the printer server says the software must be installed on each computer that runs windows. Not true, the other Windows boxes that occasionally connect to my network are easily configured to find the Printer server using the info above.

Anyway, I'm thrilled. I did notice that if I power down the printer server and start it up again that it initially won't print. To get it to print after a reboot of the printer server I need to unplug and replug the usb cable connecting the printer server to the printer.

Hope this helps someone, I looked around for a long time and couldn't find this information.

Holland

---

