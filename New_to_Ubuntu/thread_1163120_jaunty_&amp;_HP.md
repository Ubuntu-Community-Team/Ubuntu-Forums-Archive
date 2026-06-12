---
title: "jaunty &amp; HP"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-18
Since i upgraded to Juanty
i can't get my printer to print more than 5 copies with out crashing (it ends up saying after a long wait that no printer is found)
I i put 1, 2, 3 ,4 ,5 copies it is slow but will print.
it is not my printer because on the windows partition it works perfectly. HELP

---

### Post by sandyd on 2009-05-18
printer model, type of connection (usb, ethernet, printserver....) would be nice

---

### Post by DarinB on 2009-05-18
SORRY 
HP 2575 photosmart all in one
usb connection
worked great on fiesty, gutsy, hardy and intrepid!

---

### Post by DarinB on 2009-05-18
i installed hplip 3.9.4b.run 
[http://ubuntuforums.org/archive/index.php/t-1146161.html](http://ubuntuforums.org/archive/index.php/t-1146161.html)
i am trying to print 12 copies but it seems to have hung up in the middle.
at least it started to print before anything more that 5 and it led to an error that the printer is not found. 
any ideas. of what to do????

---

### Post by DarinB on 2009-05-18
CRAP! still doesn't work! now i can print more that 4 pages with out it hanging up, at least it starts then it stops. And just processes for a long time.

---

### Post by DarinB on 2009-05-18
CORRECTION **i CAN NOT PRINT MORE THAN 4 PAGES**

---

### Post by DarinB on 2009-05-18
any printer help????
How can i get people into using Ubuntu if simple stuff like printing doesn't work???????????

---

### Post by DarinB on 2009-05-18
any printer help

---

### Post by DarinB on 2009-05-18
does this mean anything to anybody
darin@darin-desktop:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 3.9.4b)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux darin-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.6.2 installed

Checking PyQt 4.x version...
OK, version 4.4.4 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.9
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.9.4b currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.4b

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-3.9.4b
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
cups-ppd-install=no
cups-drv-install=no
internal-tag=3.9.4b.10
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
error: Could not access file: Permission denied

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                    
  --------------------------------  -------------------------
  hp:/usb/Photosmart_2570_series?s  HP Photosmart 2570 series
  erial=MY5AE2216S04B8                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Photosmart-2570-series
----------------------
Type: Printer
Device URI: hp:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8
PPD: /etc/cups/ppd/Photosmart-2570-series.ppd
PPD Description: HP Photosmart 2570 Series hpijs, 3.9.2
Printer status: printer Photosmart-2570-series is idle.  enabled since Mon 18 May 2009 01:09:23 PM EDT

HP Linux Imaging and Printing System (ver. 3.9.4b)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to open /home/darin/.hplip/hp-systray.lock lock file.
warning: Unable to connect to dbus. Is hp-systray running?
Communication status: Good

Photosmart_2570
---------------
Type: Printer
Device URI: hp:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8
PPD: /etc/cups/ppd/Photosmart_2570.ppd
PPD Description: HP Photosmart 2570 Series hpijs, 3.9.4b
Printer status: printer Photosmart_2570 is idle.  enabled since Mon 18 May 2009 01:09:23 PM EDT

HP Linux Imaging and Printing System (ver. 3.9.4b)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to open /home/darin/.hplip/hp-systray.lock lock file.
warning: Unable to connect to dbus. Is hp-systray running?
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8' is a Hewlett-Packard Photosmart_2570_series all-in-one
device `v4l:/dev/video0' is a Noname UVC Camera (046d:09a1) virtual device


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


 
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x4e11 at 001:005: 
    Device URI: hp:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8
    Device node: /dev/bus/usb/001/005
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/005
# owner: lp
# group: lp
user::rw-
user:darin:rw-
group::rw-
mask::rw-
other::---



---------------
| USER GROUPS |
---------------

darin adm dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.
darin@darin-desktop:~$

---

### Post by DarinB on 2009-05-20
can anybody help me with my printing, i ordered a new printer, but i know that will not help. 
Unless the driver is a problem with my model.
i have no choice but to go to windows to print, that is embarrassing to all the people i have converted to Ubuntu. please help!!!!!!!!!!!!!!!!!!!!!

---

### Post by DarinB on 2009-05-20
Ok i got a new printer an HP 6940 a real work horse!!!!
i had one before left it to my girlfriend hers still works great, after about 4 or 5 years
now i have no problem printing multiple pages. 
which it really sucks that i can have a great printer with every version except Jaunty. then have to buy a new printer. 
if any body can still get my 2575 to work i would be really happy. now my option is to use it for a scanner only. and small jobs.

---

