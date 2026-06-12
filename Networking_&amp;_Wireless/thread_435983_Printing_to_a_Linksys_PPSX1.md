---
title: "Printing to a Linksys PPSX1"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Longwing on 2007-05-07
I've done a fair bit of googling and searching on this. Normally I wind up with at least one howto or guide which is on point. This time, no such luck.

I've a Brother HL-1440 printer attached to a Linksys PPSX1 print server. Windows and OS X have no problems printing, but not so with Ubuntu 7.04.

First I tried connecting via Network Printer UNIX LPD, no luck.
Then I tried Network Printer TCP/Socket. Still no luck.
Windows printer SMB? Access the server from there? Nope. Although it does see the linksys, it doesn't see any printers attached.

Any suggestions?

---

### Post by Jay_in_TN on 2007-05-12
The Linksys PPSX1 is an older printserver. It connects via a parallel cable to a stand-alone printer. I have the exact same printserver connected to an HP Deskjet 882C and then connected to a linksys router via a 10BT (Ethernet) cable.
Getting this printserver to work in Linux has been a never-ending source of trouble for me. 
[B]
Here is how you do it:[/B]

You need to set the IP address of the printserver to a static (not DHCP) address using the WIndows Bi-Admin software provided by Linksys.Sorry--but this needs to be done via Windows as Linksys does not offer an admin tool for Linux for this printserver.

Then when you set up a printer in Ubuntu do this:

1) Select "New Printer" from the printer admin GUI (System/Administratin/Printers).
2) Choose "Network Printer" and in the drop-down menu select "Unix Printer (LPD)."
3) For "Host" enter the static IP address of your printserver (in my case 192.168.1.110)
4) For Queue enter "L1" as the PPSX1 only connects via parallel cable (select "L2" if you have a similar product that connects via a USB cable).
5) Select "Forward"
6) Choose your printer from the list. If it is not there you can almost always select a similar printer from the same manufacturer and it will usually work fine.
7) Select "Forward" and you will have a new, default printer that should work just fine.

Thanks to hollinch for getting me started with his post in the "Print server- some help?" thread.

Hope this helps.

Jay

---

### Post by Longwing on 2007-05-14
This worked perfectly. Thanks for the help.

Incidentally, I've never needed to set up the PPSX1 through windows, I access it through the web interface ([http://192.168.1.XXX](http://192.168.1.XXX)) where XXX is the server IP.

---

### Post by Jay_in_TN on 2007-05-21
Thanks for the tip on accessing the print server through the browser. I didn't know that.
Jay

---

