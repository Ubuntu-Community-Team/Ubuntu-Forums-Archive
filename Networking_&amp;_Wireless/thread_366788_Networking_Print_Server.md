---
title: "Networking Print Server"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by DJNOVA2006 on 2007-02-21
Hey guys im in need of some help. Im not a total Ubuntu noob but might as well be. Ive got 3 pc's, 2 winXP and one on Ubuntu 6.10 Desktop. Xp's are on wireless and the Ubuntu is lan'd to the wireless router. What i want to do is to use the ubuntu machine to be like a print server, i want to wirelessly print from either of my xp machines. I have an Hp Photosmart C4180 all in one. If u need any more spec just let me know. And any feedback and help is muchly apreciated.

DJNOVA2006

[email]djnova2006@hotmail.co.uk[/email]

---

### Post by charles.g.moore on 2007-02-21
I think it may just be a matter of installing cups (which you probably already did) and adding an ipp printer through the winXP add printer wizard.

Not to take credit this is an excerpt from: [http://ubuntuforums.org/showthread.php?t=268245](http://ubuntuforums.org/showthread.php?t=268245)
 
Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(Dapper: /etc/cups/cups.d/ports.conf; Edgy: /etc/cups/cupsd.conf)
Code:

#Listen localhost:631 Listen *:631 Listen /var/run/cups/cups.sock

Restart the cups daemon:
Code:

sudo /etc/init.d/cupsys restart

On the Windows box:

   1. Start the Add Printer wizard
   2. Click Next
   3. Select A network printer, or a printer attached to another computer
   4. Select Connect to a printer on the Internet or on a home or office network
   5. Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the URL box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. Don't forget the port number!
   6. Click Next and run through the driver installation to complete

---

