---
title: "How to connect a USB printer to a Router (Fritz Box)"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by bhogal on 2008-11-29
[SIZE="3"]Hello,

I would like to know how to connect a printer to a Router Fritz Box. I have a Fritz Box 7270 which has a USB port. In windows it works (Which I don want to use). 

Under [www.avm.de](www.avm.de) (fritz Box) they have mentioned to use option "Raw TCP" and port 9100. 

When I go under System>Administration>Printing. I choose new printer and then there the following options.

LPT #1
Serial Port #1
AppSocket/Hp JetDirct
Internet Printing Protocol (ipp)
LPD/LPR Host or Printer
Windows Printer via Samba
other

I have no clue which one to take. I have tried ipp but no luck. I have a Samsung ML1610. [/SIZE]

---

### Post by thehayro on 2008-12-01
Hello


You have to choose "AppSocket/Hp JetDirct" and enter the IP Address of your FritzBox! router. the port is 9100, but i assume it is already entered in that Port-field.

if there are any problems, just let me know :)

greetz

thehayro

---

### Post by bhogal on 2008-12-02
[SIZE="2"]Hello thehayro,

thx for your reply, I have tried it and it gives a message printer not ready and network busy. what should be the location.

screenshot attached.[/SIZE]

---

### Post by Hagar@007 on 2009-05-24
This set-up worked for me great (Canon Pixma iP5000), but I noted with my previous attempts of entering the correct setting, the printer had disabled itself.  Perhaps you could verify the Printer is still enabled, if it is - Disable it and re-Enable it.

I also went to the USB device page of the Fritz!Box, enabled Remote access for USB devices and Unticked it again - then all seemed to work - I am not sure if this has any impact, but on my previous installation of Ubuntu, I also performed this action, and also thereafter it worked!!  -  It may be that the Fritz!Box requires some kind of USB reset, and this is activated by this action.

Good-Luck
Hagar

---

### Post by Sven6210 on 2010-05-17
Go to: System - Administration - Printing

Klick: New

Choose: Network Printer

Choose:
AppSocket/HP JetDirect
Host: fritz.box
Port: 9100

Then choose the right printer. You should use the same printer driver that you would when connecting the printer via USB to Ubuntu.

For my Samsung ML-2010 this worked perfectly.

---

