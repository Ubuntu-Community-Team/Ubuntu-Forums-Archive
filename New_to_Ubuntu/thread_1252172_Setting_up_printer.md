---
title: "Setting up printer"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Arla on 2009-08-28
Not sure if anyone can help,

So I have a ML=-1740 printer, and I'm connecting it via USB to my laptop.

All reports I've read say that it should be auto-detected, but it's not (not sure if that's possibly because I'm using Karmic or not?)

Now yesterday in my digging I found a terminal command that did list the printer (but of course today I can't find that command, nor do I recall what it was) can anyone offer a newbie advice on steps to follow to see if it's a CUPS bug, or me being thick or what?

Edit:

Found the program, it was lsusb, it reports

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04e8:324c Samsung Electronics Co., Ltd ML-1740 Printer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:0892 Logitech, Inc. OrbiCam
Bus 001 Device 003: ID 1025:2228 Hyper-Paltek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


As can be seen, the printer is shown (Bus 003 Device 004), but CUPS, even after a restart, doesn't seem to even see USB as possible?

---

### Post by MrWES on 2009-08-28
> **Arla said:**
> Not sure if anyone can help,

So I have a ML=-1740 printer, and I'm connecting it via USB to my laptop.

All reports I've read say that it should be auto-detected, but it's not (not sure if that's possibly because I'm using Karmic or not?)

Now yesterday in my digging I found a terminal command that did list the printer (but of course today I can't find that command, nor do I recall what it was) can anyone offer a newbie advice on steps to follow to see if it's a CUPS bug, or me being thick or what?



Edit:

Found the program, it was lsusb, it reports

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04e8:324c Samsung Electronics Co., Ltd ML-1740 Printer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:0892 Logitech, Inc. OrbiCam
Bus 001 Device 003: ID 1025:2228 Hyper-Paltek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


As can be seen, the printer is shown (Bus 003 Device 004), but CUPS, even after a restart, doesn't seem to even see USB as possible?

Maybe try configuring via the web gui? See if you can add the printer from there: 
[http://localhost:631]("http://localhost:631")

---

### Post by Arla on 2009-08-28
Nope, I get these options

SCSI Printer
Serial Port #1
LPT #1
HP Printer (HPLIP)
HP Fax (HPLIP)
Discovered Network Printers: 	(None)
Windows Printer via SAMBA
AppSocket/HP JetDirect
Backend Error Handler
Internet Printing Protocol (http)
Internet Printing Protocol (ipp)
LPD/LPR Host or Printer
	

This is on Cups 1.4.0

---

### Post by MrWES on 2009-08-28
> **Arla said:**
> Nope, I get these options

SCSI Printer
Serial Port #1
LPT #1
HP Printer (HPLIP)
HP Fax (HPLIP)
Discovered Network Printers: 	(None)
Windows Printer via SAMBA
AppSocket/HP JetDirect
Backend Error Handler
Internet Printing Protocol (http)
Internet Printing Protocol (ipp)
LPD/LPR Host or Printer
	

This is on Cups 1.4.0

You might want to check this site to see if your printer is supported via a USB connection:
[http://www.openprinting.org/printer_list.cgi]("http://www.openprinting.org/printer_list.cgi")

---

