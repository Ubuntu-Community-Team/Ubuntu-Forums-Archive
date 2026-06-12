---
title: "Printing remotely via CUPS isn't working - Prints @PJS Information"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by Jonny_Morrison on 2014-03-29
Hello!

(Not sure if this is in the correct forum area)

Okay, so I have Ubuntu Desktop 12.04. It functions as a web server, which runs fantastically. I'm trying to get it set up as a print server, so I installed CUPS.

My printer, the *Dell 1250c* doesn't have a Linux driver, however, after a quick google search I found that the Xerox Phaser 6000b linux driver works, so I installed that. I can print from my Ubuntu machine via USB and it works perfectly. So, I added the printer to CUPS, setting the driver as the Xerox one. The printer is also shared over the network as a Samba share.

On my Windows 7 PC, which has the 1250c driver installed (was connected via USB to that one) and connected via [http://serverip:631/printers/Dell_1250c](http://serverip:631/printers/Dell_1250c) and selected the already installed 1250c driver for this. I try to print a PDF, and it prints a page of code, the first few lines of which are:

> 
-12345X@PJL JOB MODE=PRINTER
@PJL SET STRINGCODESET=UTF8
@PJL COMMENT DATE=03/29/2014
@PJL COMMENT TIME=13:56:41
@PJL COMMENT DNAME=Test Page
@PJL SET JOB ATTR="@LUNA=User"
@PJL SET COPIES 1
@PJL SET QTY=1
@PJL SET JOBATTR="TRCH=OFF"
@PJL SET DUPLEX=OFF
etc......


So, I then tried connecting directly to the Samba Share. The same thing happened.

Then I thought that maybe it was due to the disagreement between the 1250c Driver on the W7 Client and the 6000b driver on the Ubuntu Server. So, I installed the 6000b driver to the W7 Client and set the printer to use that driver. The same thing happened.

Next, I tried to connect via a macbook running OS X, also with a 1250c driver installed. I tried to add the printer via IP, but it could not find the printer on either
**ipp://*serverip*/printers/**[I]**printername**
[/I]Or
**[http://*serverip:63](http://*serverip:63)**1*/printers/**[I][B]printername
[/B]
[/I]So, I tried to connect via the 'Windows' option, which quickly found the server and the printer. However, when trying to print on that, something would be send (PrinterProxy would come up [the mac's printer queue]), but nothing would print. A job would come up on the Ubuntu queue very quickly, but it was evidently empty. Occasionally, it would also print the same @PJL information that Windows 7 would. 

HOWEVER, the mac DID find the printer via **Bonjour**. Printing through this **works**! Horrah! So, either, how do I fix the ipp/http/samba share to get it to work with Windows 7 OR, how do I connect Windows 7 to the printer via Bonjour. I only need this on a local network and I don't mind the method!

Many hours have been wasted on something that should have been the simplest thing in the world.
Many many thanks in anticipation.

Jonny M :)

---

### Post by Jonny_Morrison on 2014-03-29
Okay, so I downloaded Bonjour Print Services to the Windows 7 Client, which immediately found the printer. However, it still only prints that @PJL code.

Jonny

---

### Post by houstonbofh on 2014-03-29
This is a well known issue with Windows printing that if faithfully reproduced in Samba.  Jobs can be sent as emf or raw, and it is never clear which is which.  You are sending a preprocessed job, and the print server is processing it.

So, this is the solution for that...
> [https://en.opensuse.org/SDB:Printing_from_Windows_to_Linux](https://en.opensuse.org/SDB:Printing_from_Windows_to_Linux)

Enforce "raw" printing

When Windows clients run the printer-specific driver, they send printer-specific data.

There is no reliable working automatic way to detect whether data which is sent to CUPS is printer-specific data (which should be sent directly to the printer) or data which must be filtered to get printer-specific data. For examle when it is a PostScript printer, its printer-specific data is PostScript but by default PostScript data is filtered by CUPS.

Therefore when Windows client systems send printer-specific data, the CUPS server must be forced to send the data directly to the printer and not attempt filtering what is already printer-specific data.

This is called "raw" printing. CUPS can be forced to do raw printing by using the "-o raw" switch in the printing command ("lp -d queue_name -o raw").

Samba has by default the following option in /etc/samba/smb.conf to enforce raw printing:

cups options = raw

This way, Samba, which gets the printer-specific data via SMB, forwards it in raw printing mode to the print queue so that CUPS sends it directly (without additional filtering) to the printer. 

Next is how you connect and drivers.  Since you are using samba anyway, and you have Windows systems...
[https://wiki.samba.org/index.php/Samba_as_a_print_server#Uploading_printer_drivers_for_Point.27n.27Print_driver_installation](https://wiki.samba.org/index.php/Samba_as_a_print_server#Uploading_printer_drivers_for_Point.27n.27Print_driver_installation)

---

