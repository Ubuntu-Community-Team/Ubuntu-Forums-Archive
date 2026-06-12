---
title: "Invisible Ethernet Printer"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by rdagijones on 2007-08-23
I have a Lexmark Z65n printer connected to a D-Link wireless router via an ethernet port on the printer.  My Ubuntu box is connected to the D-Link by wire and I have two laptops that print by wireless connection.  I have tried setting up CUPS to no avail.  The main problem seems to be that the Ubuntu box does not find the printer in the network.  **Is there some way that I could configure DHCP or something so that the printer would show up?**

---

### Post by stinger30au on 2007-08-23
try the laptops via cable and see if they work. elimination of baddies

---

### Post by livestockPimp on 2007-08-24
How is the printer set up? are you running it through a print server or is it a network printer.
What OS are you using on the laptops (i assume they are working)
how is CUPS configured? ie; using socket://, lpd://, ect. what driver is CUPS using? does it have the correct driver for that model or are you using a generic driver for it?

---

### Post by livestockPimp on 2007-08-24
also, it is generally better to have a static IP for printers so you can refer to them by IP address, using netbios names can be unreliable.

---

### Post by rdagijones on 2007-08-24
The Ubuntu box is connected to the D-link via LAN.  Also connected to the D-link is the Lexmark Z65n ethernet printer.  I actually have a dual boot with a Windows hard drive and an Ubuntu hard drive.  When booted into windows it prints just fine.  The two laptops are wireless with Windows installed and they also print through my home network.

As for the driver, I tracked it down through Lexmark.  All of the documentation that I read refers to a USB connection.  I do not want to use the USB so that the laptops can print even it the Ubunbu box is not on.  the Lexmark Windows and Mac Lexmark Z65n drivers come with a handy "Lexmark Network Configuration" application that detects the network printer for you.  It is a snap in either of those OS's.  With the tool I can and have assigned a static IP address [192.168.0.128] for the printer.  Even more, I have give the printer a static DHCP in the D-Link set up.  (Needless to say, the printer's IP address is not changing.)

Any ideas?

---

### Post by livestockPimp on 2007-08-26
ok,
I would suggest getting the port on the printer you are meant to send print jobs to, this is generally 9100, but one some printers it is different. Then create a new printer in CUPS from the admin menu, for the communication dropdown box choose "hp/ socketjet" (or similar) then for the next screen put "socket://192.168.0.128:9100" (change 9100 for the port you looked up before). For the make/model section choose a "HP Laserjet generic foomatic" I cant remember exactly what it is listed as but should read something similar to that. 

Also, remember that after you have set it up with those paramaters go to the "printers" tab at the top and select "printer configuration" underneath the printer and then change the paper size to the correct setting.

This should hopefully work, I know you told me this is a Lexmark but HP drivers are VERY generic with most laserjets and should work like this.

---

### Post by livestockPimp on 2007-08-26
to get the port number the printer is printing on it will either be in the web interface under network settings or if you print out the network config page then it is generally listed here.

---

### Post by rdagijones on 2007-08-26
I have tried the instructions that you gave with the port 9100 and nothing.  The LexmarkZ65n has no web interface.   In Windows, Lexmark has a proprietary "Lexmark Network Configuration" utility for locating the printer and reassigning the IP address.  It seems that, in Windows, the Lexmark software creates a new printer port called "Lexmark_Z65_1bb969"  (The last six digets "1bb969" are the last six of the MAC address for the printer).   Is there some way to use the IP address and the MAC address to direct to the printer?

I looked up the instructions for printing out the network config page.  There is no port listed.   This is the information printed
Build Date: 04/19/02
Time: 13:26:45
Path: \BUILD\D
Code Level: DubR2.0
Date: 04/19/02
Page count: 1/762
Last Error: 51 04 0C 01
At Address: CB
Temps K: 41
CMY : 45
AMB: 27
USB Serial Number: 19D006003101293
IP: 192.168.000.128
Mode: Auto
MAC: 0020001BB969
MFG: Lexmark
CMD CPDNPA001
Model: Lexmark Z65
Class: Printer
DES: Lexmark Z65
USB Vendor ID: 0x043D
USB Product ID: 0x001A

---

