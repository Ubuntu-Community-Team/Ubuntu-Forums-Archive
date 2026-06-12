---
title: "Endless Print Jobs to Linksys WPS54GU2 print server"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by troutbum on 2005-07-27
Every print job sent to my Linksys server prints endless copies.

I am connected to a Brother HL-1440 laser printer via a Linksys WPS54GU2 print server.  

I am creating a new printer via Network Printer>CUPS Printer (IPP)>url http://xx.xx.xx.xx:631/ipp/P1>Brother HL-1440>hl1250 (recommended). 

The printouts look great but they keep on coming and coming.  The only way
to stop to flood of paper is to cancel the print job in Ubuntu.

It appears that Ubuntu does not understand that the job has been sent and
successfully received by the print server.  

I tried that turning on "LAN detection" in the Global Settings but this did
not help.

I tried the other drivers listed in Ubuntu with the same results.  I also went to the Brother website to create a PPD file with no success.

I'm concluding that the problem is occurring between Ubuntu and the Linksys Print Server.  The laser printer does not seem to be the issue.

I brought up the WPS54GU2 administration page in my web browser.   Under the TCP/IP settings, I reduced the reconnection attempts to 0 from 254.

This change has prevented more than 1 copy from being printed.  However, the job remains stuck in the Ubuntu queue for the printer.  The printer icon says the status is "Printing 1 Jobs".  Right-click the printer icon>properties says "Printing: Printer does not support IPP/1.1, trying IPP/1.0..."

Because the first print job gets stuck, all subsequent print jobs can't get through.  The workaround is to manually cancel each job after it prints.

It seems that Ubuntu is not getting the message that the print job has been received.

Does anybody have any ideas on how to fix this?  Thanks!

---

### Post by KageKeeper on 2005-07-27
I have an HP DeskJet 6540 installed on my USB port on my Ubuntu box. I also have a Windoze XP machine on the LAN.

CUPS is installed and correctly configured as I can print from the localhost as well as the networked machine.

The problem is, the print queue is not automatically cleared when a doc finishes printing. I have to manually cancel the job before something else can be printed.

Any ideas?

---

### Post by troutbum on 2005-08-03
UPDATE:  I am able to print without any problem to my Brother HL-1440 laser printer by directly connecting to the printer with a USB cable.  I am using the default
driver hl1250 (recommended).

The Brother HL-1440 allows you to use both USB and parallel ports simultaneously.
My Linksys WPS54GU2 print server is connected via the parallel port.  

It looks like the problem with printing endless copies is isolated to connecting
Ubuntu 5.04 with the Linksys WPS54GU2 print server.

---

### Post by jhuff on 2005-10-04
I have finally got my Brother HL-1440 printer working after I installed the Linksys PrintServer PSUS4.  It was not easy to get working with the windows computers connected to my network, but I finally did get it working.  I am connecting the server to a Belkin wireless router (this could be one of my problems).  I must have turned everything on an off a dozen times trying to get everything squared away.  I did set a static IP address for the server becuase I was getting network address conflicts.  So I am still at a loss as to how I finally got the windows computers working correctly.  As far as my linux box I did the following:

Added a new printer using "Unix Printer (LPD)"
        Host = Server IP address (192.168.2.xxx)
        Queue = L1

I initially tried using CUPS Printer (IPP) but whatever I printed just kept printing multiple copies until I cancled the print job.

It was easier getting my linux box working then the windows computers.

I still can't believe I got my printer working.  I have been trying for months to get the Brother HL-1440 to work.  It had been shared from a windows computer.  Now I can finally move totaly away from Windows!!  I am totaly impressed with Breezy Badger.

---

