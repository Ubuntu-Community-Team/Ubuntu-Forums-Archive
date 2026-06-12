---
title: "Sharing printers with Windows XP in VirtualBox"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by phubert28 on 2010-08-12
64 bit Ubuntu 10.4 - VirtualBox 3.2.8

I have ONE software package, Dymo's address book and label design software, that runs only under Windows (and maybe Mac, but NOT Linux).

I have the Linux Dymo driver installed and can PRINT labels, but I need to be able to use my Dymo ADDRESS book and online address correction (zip + 4) software.

So far, although VirtualBox passes-through the Dymo Labelwriter 400 Turbo definition TO Windows, nothing prints. The spool queue clears, but ZIP actually reaches the printer.

My next thought has been to SHARE the devices defined on my 64 bit Ubuntu 10.4.

I am hard connected to a Netgear router.

I can PING the IP address of my Ubuntu machine, but when I use the NAME it resolves to what appears to be the external address shown by my ISP.

Is there anything I can do on the Linux side to enable the virtual XP to see the printers?
(the Dymo is USB attached, my HP is tcp/ip connected)

---

### Post by drdos2006 on 2010-08-12
You need to know the IP address of your Ubuntu machine. for instance, 192.168.0.2 You also need to know what your printer is called on your Ubuntu machine. Windows XP would then install the printer via XP Printer and Faxes setting. the printer would be installed as : [http://192.168.0.2:631/printers/Canon-6300](http://192.168.0.2:631/printers/Canon-6300) for instance.

From the terminal find your IP. Type :  ifconfig. Note the IP address.
Use your browser with :  [http://localhost:631](http://localhost:631) to run CUPS, go to Printers and note the printer queue name.

From XP go to Start, Printers and Faxes, add new printer.
Fill in details with port http://<your IP>:631/printers/<your printer>

regards

---

### Post by phubert28 on 2010-08-13
Well, you pointed me in a better direction, but Windows was unable to connect.

I'd setup TCP/IP printer ports, but never before used the "Connect to a printer on the Internet or on a home or office network:" radio button (tho I worked primarily with Windows SERVERS, not workstations!).

I can successfully PING the Ubuntu machine's IP address, so I'm wondering if it could be a permissions issue.

Tried both the IP-attached HP and the Dymo.

From System > Administration > Printing, the HP's access control is already set to allow printing from everyone, tho.

***

O.K. I think I've GOT it: I had to set CUPS to allow printing from the Internet... don't know I LIKE that one, but...

---

### Post by drdos2006 on 2010-08-13
Good work, dont forget to mark your thread [SOLVED].
regards

---

### Post by phubert28 on 2010-08-13
Just did. Will have to SAVE all that for my Tomboy notes! The ongoing saga of conversion to Linux!

:-D

---

### Post by phubert28 on 2010-08-13
Couple of extra notes, tho:

For the HP printer, I needed its driver disk
For the USB-attached Dymo, NOTHING more was needed

COOL!!!!!

DOUBLE thanks!!!

---

