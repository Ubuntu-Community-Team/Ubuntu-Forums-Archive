---
title: "HP Photosmart C7280 help"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by Rich Bruski on 2010-04-05
Hi:
I'm new to Ubuntu.. I'm trying to install my scanner, which is part of a HP 4 in 1 printer.  The printer works fine but, the XSane image scanner program will not recognize my scanner.  (HP Photosmart C7280)
I've downloaded and installed  the newest hplip.  Followed instructions, turn off printer, unplug printer, rebooted the system, and anything else I could think of.  The hplip program seemed to install okay.
Any help would be appreciated.
Rich Bruski

---

### Post by kellemes on 2010-04-06
As far as I know your multifunction-printer *should* be working perfectly.

You installed hplip from the hp website? Or using the Ubuntu packagemanager?
The scanner of my Photosmart C6380 didn't work until I installed the latest hplip from the hp website.
[http://hplipopensource.com/hplip-web/downloads.html]("http://hplipopensource.com/hplip-web/downloads.html")

Let us know if you need any help..

---

### Post by Rich Bruski on 2010-04-06
Thanks for the response.
I installed the HPlip from the HP website.  It was supposed to be the latest.  I'll keep trying.
Rich Bruski

---

### Post by BrokeMahPC on 2010-04-06
How are you trying to scan?
For me with an HP Photosmart Plus and Ubuntu Lucid you have to open simple scan (really great), Xsane, or HPlip - Actions and select Scan.
The Scan button on the printer does not do anything - you have to initiate it from the PC.

Also:
I think this now comes as part of HPlip but for an all in one printeryou need to get these from System - Administration - Synaptic Package Manager:
HP Linux Printing and Imaging - gs IJS driver (hpijs)
HP Linux Printing and Imaging - HPIJS PPD files

search synaptic for hpijs, hpijs-ppds and check these are installed.

also search "linux printing" on the web and on HP's site and check your printer is supported.

---

### Post by Rich Bruski on 2010-04-06
I made sure that the printer is supported.  The printer works fine.  When I try to open xsane I get the error message that no scanner was found.
Xsane will not open and allow me to load a driver for the scanner???

---

### Post by kellemes on 2010-04-07
You're working wireless?
In that case, does xsane find the scanner when connected through USB?

---

### Post by mykrob on 2010-04-26
in the terminal, run the command:

hp-makeuri <IP ADDRESS OF PRINTER>

it will spit out something like

```

HP Linux Imaging and Printing System (ver. 3.10.2)
Device URI Creation Utility ver. 5.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

CUPS URI: hp:/net/Photosmart_Plus_B209a-m?ip=192.168.10.50
SANE URI: hpaio:/net/Photosmart_Plus_B209a-m?ip=192.168.10.50

```

the piece of code next to "SANE URI" will need to be entered into you command for xsane in your menu entry.

For example,

xsane hpaio:/net/Photosmart_Plus_B209a-m?ip=192.168.10.50

---

### Post by mykrob on 2010-04-26
just tested, it works with simple-scan too

simple-scan hpaio:/net/Photosmart_Plus_B209a-m?ip=192.168.10.50

---

### Post by JCyberinux on 2010-08-30
[I]try the gui 

sudo apt-get install hplip-gui

[/I]You can then find it under System&#8594;Preferences&#8594;HPLIP Toolbox

maybe can solved the issue easier.

Cheers!

---

