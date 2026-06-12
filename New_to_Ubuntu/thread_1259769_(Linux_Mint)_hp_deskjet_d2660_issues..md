---
title: "(Linux Mint) hp deskjet d2660 issues."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by verrlara on 2009-09-06
It is trying to literally print to pdf when I am asking it to do a standard printing job. Which in turn prints gibberish that is not what I was intending to get.

---

### Post by k33bz on 2009-09-06
when you push to print it should give you an option to either print to pdf or to your printer if it is hooked up. Does your computer see the printer?

---

### Post by halitech on 2009-09-06
did you install hpijs or hplip before installing the printer?

---

### Post by verrlara on 2009-09-06
I installed the printer via hplip. Let me get you my configuration options. I build it from source. 

```
./configure --enable-foomatic-rip-hplip-install --enable-hpijs-install --enable-dependency-tracking --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install  --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build

```

Install went fine. There was no screaming for dependences. The version of hplip is 2.9.8 that I installed. I think it is wanting to print to pdf instead of going through the pdf to ps process.

---

### Post by verrlara on 2009-09-06
It is also giving me flashing lights at the moment. The little paper icon with the red arrow, and both of the ink leds are flashing. But I am pretty sure it isn't out of ink. And it has plenty of paper. o.o;; It was complaining of communication errors.

---

### Post by verrlara on 2009-09-06
bump

---

### Post by verrlara on 2009-09-08
bump

---

### Post by halitech on 2009-09-08
try opening CUPS ( [http://localhost:631](http://localhost:631) ) and see if the printer is installed there. If it is, delete it and then readd it.

---

### Post by verrlara on 2009-09-09
Printer was there on cups. It gives me blinking lights and doesn't do anything. No gibberish since I installed python-notify and policykit which hp-setup -g had been complaining about not having. Just blinking lights. On off button, add paper and ink carterage lights. Ink is new, paper is full, usb is connected.

Looked again at cups and it said in quotes 
[B]> /usr/lib/cups/backend/hp failed

[/B]No idea what that means for me though.

---

### Post by verrlara on 2009-09-09
Gave me gibberish again. The literal coding for a pdf document. It thinks it is a pdf printer when it should be converting to postscript I think? Is there anyway to tell it to print postscript and not think it is suppose to print pdf?

---

### Post by verrlara on 2009-09-09
Hope these codes help you :D 

```
hp-check -t

HP Linux Imaging and Printing System (ver. 3.9.8)
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
Linux Annas-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Distribution:
linuxmint 7

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

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
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
HPLIP 3.9.8 currently installed in '/usr/local/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.8

[dirs]
home=/usr/local/share/hplip
run=/var/run
ppd=/usr/local/share/ppd/HP
ppdbase=/usr/local/share/ppd
doc=/usr/local/share/doc/hplip-3.9.8
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/local/share/cups/drv/hp

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
hpijs-install=yes
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=yes
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.9.8.36
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=no


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
eula = 1
installed = 1



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = Deskjet_D2600
working_dir = .
device_uri = "hp:/usb/Deskjet_D2600_series?serial=TH95G2452305C9"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.8.36
date_time = 09/08/2009 23:24:55

[settings]
systray_messages = 0
systray_visible = 0

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
device_list = 
interval = 5



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                  
  --------------------------------  -----------------------
  hp:/usb/Deskjet_D2600_series?ser  HP Deskjet D2600 series
  ial=TH95G2452305C9                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_Deskjet_D2600_series_USB_TH95G2452305C9_HPLIP
------------------------------------------------
Type: Printer
Device URI: hp:/usb/Deskjet_D2600_series?serial=TH95G2452305C9
PPD: /etc/cups/ppd/HP_Deskjet_D2600_series_USB_TH95G2452305C9_HPLIP.ppd
PPD Description: HP Deskjet d2600 Series hpijs, 3.9.8.36
Printer status: printer HP_Deskjet_D2600_series_USB_TH95G2452305C9_HPLIP is idle.  enabl/usr/lib/cups/backend/hp failed00 PM MDT
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname Macally USB2.0Camera virtual device


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

HP Device 0x8011 at 001:013: 
    Device URI: hp:/usb/Deskjet_D2600_series?serial=TH95G2452305C9
    Device node: /dev/bus/usb/001/013
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/013
# owner: lp
# group: lp
user::rw-
user:verrlara:rw-
group::rw-
mask::rw-
other::---



---------------
| USER GROUPS |
---------------

verrlara adm dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.

``````



/usr/lib/cups/backend/hp
direct hp:/usb/Deskjet_D2600_series?serial=TH95G2452305C9 "HP Deskjet D2600 series" "HP Deskjet D2600 series USB TH95G2452305C9 HPLIP" "MFG:HP;MDL:Deskjet D2600 series;CLS:PRINTER;DES:Deskjet D2600 series;SN:TH95G2452305C9;" 
``````
hp-info


hp-info

HP Linux Imaging and Printing System (ver. 3.9.8)
Device Information Utility ver. 5.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/Deskjet_D2600_series?serial=TH95G2452305C9


Done.

```

---

### Post by halitech on 2009-09-09
sorry but the codes don't mean much to me. Not sure why its not working, generally HP pretty much works as soon as you plug it in and install hplip or hpijs. Did you try removing it and readding it?

---

