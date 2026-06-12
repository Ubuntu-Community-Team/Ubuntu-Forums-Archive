---
title: "Networked Printing + PDFs"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Warhamster on 2008-03-21
Firstly, long time lurker/reader, and that's always solved my problems. I love you guys/gals!

Now the problem...

I've got a Ubuntu 7.10 Server box (2.6.22-14-server kernel) with an HP PSC1410 printer connected to it. It's shared over the network with Samba. I can print everything fine locally (PDFs, etc) but for some reason clients (XP Laptop, Vista Laptop, Vista Desktop) cannot print PDFs to it. Word documents etc work fine when printed to it - albeit a little slow.

I've tried a couple of things - removing the printer from the box and reinstalling, trying different client drivers (just using the inbuilt 1400 series drivers on Vista - they worked fine when the printer was connected to it) - all that sort of thing.

Here's my printer portion of my smb.conf - just yell if you want anything else. 

```

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
   use client driver = yes
```

Thanks Ubuntu-ians!

---

### Post by drdos2006 on 2008-03-21
Try this from the CUPS.conf file....
Sharing Printers
Once the user is connected to the network drive, the printer should be able to be seen from the Windows box. 
Select “My Network Places” -> “Computers Near Me” -> the Linux box. 
Windows will require the Windows drivers for the respective printer. 

To enable the printing process from a Windows network, the CUPS configuration file needs to be added to.
Stop CUPS from the menubar.
Select “System” -> “Administration” -> Services”.
Untick the box “Printer service (cupsys)”, close and save.

From the menubar on the Linux box, 
select  “Applications” -> “Accessories” -> “Terminal” and  type the following command.

sudo gedit /etc/cups/cupsd.conf

Look for : 
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all

Add the following line:
	BrowseProtocols all
You may also have to change this section in your cupsd.conf file

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 192.168.1.12:631

(192.168.1.12 is the IP address of the machine with the printer on it, 631 is the port number to listen on)

You then connect your other machine to that printer using an internet printer type of connection with the IP address, the port number.
Save the file and close, restart the printing service.

Start CUPS from the menubar.
Select “System” -> “Administration” -> Services”.
Tick the box “Printer service (cupsys)”, close and save.

From the Windows box, print a test page.

regards

---

### Post by Warhamster on 2008-03-21
Yep, I got all of that.

The test page prints fine, but I still cannot print .pdfs from the remote machines. I've tried 3 different machines and when I print a pdf it just goes *poof* and disappears, with nothing said by either machine. Everything prints correctly from other programs - eg; Word, Powerpoint - but not Foxit or Adobe Reader....

---

### Post by drdos2006 on 2008-03-21
Maybe try XPDF or EVINCE. See if that solves the problem.

regards

---

