---
title: "new hp photosmart plus won't print pdf's"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by cloyd on 2010-04-18
I just bought a new hp photosmart plus209b a few days ago. It has worked well until tonight. I'm a little late getting ready for april 15th, and I was happily printing some credit card statements I had downloaded as pdf's. Suddenly, the printer would no longer print. I noticed that the processor was getting warmer (about 60) and it was running at 100%. I've rebooted, shut the machine and printer down, (while the printer was down, and disconnected the power for about 5 minutes). Still, on pdf's, it is a no go.  Interestingly enough, it prints open office word processor documents, and I printed a picture, just to see. Worked fine. Just not pdf's. 

I need to print these pdf's.   
 

The black cartridge is shows half full.  Colors are all full. Do I need to replace the black? I hate to, when it is half full. If this is a common cure, I'll try it, though ink is expensive.

EDIT: I realized I can open pdf's with other programs. Gimp and XPDF. These will print.




Below is the output of **hp-check -t** 


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
Linux steve-UbuntuSuperNetbook 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 9.10

Checking Python version...
OK, version 2.6.4 installed

Checking PyQt 4.x version...
error: NOT FOUND OR FAILED TO LOAD!

Checking for CUPS...
Status: scheduler is running
error: Version: (Not available. CUPS may not be installed or not running.)

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
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers

Checking for dependency: CUPS devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd

Checking for dependency: CUPS image - CUPS image development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsimage2-dev

Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libdbus-1-dev

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes build-essential

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes openssl

Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libjpeg62-dev

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsnmp-dev

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libtool

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libusb-dev

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-qt4-dbus

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-dev

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-reportlab

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.9.8 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.8

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.9.8.36
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
device_uri = hp:/usb/Photosmart_Plus_B209a-m?serial=CN02O3227905CS

[installation]
date_time = 04/18/2010 18:40:09
version = 3.9.8.36



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                     
  --------------------------------  --------------------------
  hp:/usb/Photosmart_Plus_B209a-m?  HP Photosmart Plus B209a-m
  serial=CN02O3227905CS                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
-2600-Series
------------
Type: Unknown
Device URI: usb://Lexmark/2600%20Series
PPD: /etc/cups/ppd/-2600-Series.ppd
PPD Description: Lexmark 2600 Series, 1.0
Printer status: printer -2600-Series is idle.  enabled since Wed 07 Apr 2010 01:53:28 PM CDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

My_Lexmark_2600_Series
----------------------
Type: Unknown
Device URI: lxkusb://Lexmark/2600%20Series
PPD: /etc/cups/ppd/My_Lexmark_2600_Series.ppd
PPD Description: Lexmark 2600 Series, 1.0
Printer status: printer My_Lexmark_2600_Series is idle.  enabled since Wed 07 Apr 2010 03:12:14 PM CDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

Photosmart-Plus-B209a-m
-----------------------
Type: Printer
Device URI: hp:/usb/Photosmart_Plus_B209a-m?serial=CN02O3227905CS
PPD: /etc/cups/ppd/Photosmart-Plus-B209a-m.ppd
PPD Description: HP Photosmart Plus b209a-m hpijs, 3.9.8
Printer status: printer Photosmart-Plus-B209a-m is idle.  enabled since Sun 18 Apr 2010 06:28:42 PM CDT

HP Linux Imaging and Printing System (ver. 3.9.8)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname CNF9011 virtual device
device `hpaio:/usb/Photosmart_Plus_B209a-m?serial=CN02O3227905CS' is a Hewlett-Packard Photosmart_Plus_B209a-m all-in-one


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

HP Device 0x7e11 at 001:004: 
    Device URI: hp:/usb/Photosmart_Plus_B209a-m?serial=CN02O3227905CS

HP Linux Imaging and Printing System (ver. 3.9.8)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?
    Device node: /dev/bus/usb/001/004
    Mode: 0664

---------------
| USER GROUPS |
---------------

steve adm dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

error: 18 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd
sudo aptitude install --assume-yes libcupsimage2-dev
sudo aptitude install --assume-yes libdbus-1-dev
sudo aptitude install --assume-yes build-essential
sudo aptitude install --assume-yes openssl
sudo aptitude install --assume-yes libjpeg62-dev
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libtool
sudo aptitude install --assume-yes libusb-dev
sudo aptitude install --assume-yes python-qt4-dbus
sudo aptitude install --assume-yes python-dev
sudo aptitude install --assume-yes python-reportlab
sudo aptitude install --assume-yes libsane-dev

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.


I'm going to keep looking, and check back here frequently. All and any help will be appreciated.

---

### Post by cloyd on 2010-04-18
Ok, here's the update. I checked HP site, and they said I needed hplip 3.10.2, which I didn't have. So I installed it. After about 20 minutes downloading, it worked . . . for images, for open office, but not for the document viewer.  I think I need to clarify. It is document viewer. I found that other programs will open PDF's, and they will print. I am wondering if the problem is not with document viewer.  


Oh, yes, I ran hp check again, and in the summary section, it said "2 errors or warnings." They were not specified.  My immediate problem is taken care of, but how do I print from document viewer?  It still can run my cpu up to 100% and 60 degrees . . . sometimes, when I cancel the print job, the cpu goes down. Sometimes, it doesn't. When that happens, I have to reboot..

Here is another update added the morning after this rest of this was posted: I went to the office, and tried printing on my Lexmark x2600 which is one of the few lexmarks with linux support. Surprisingly, it printed from open office, and from Document Viewer. So, the problem is most likely not in Document Viewer, but with the hp drivers. 

Anther interested thing that I left out earlier. Just before this whole problem started, I had just finished printing a pdf document, and then, the printer printed out two pages or black and white gibberish . . . pages filled with horizontal black strips, and the black was composed of small irregular spots.  

Printer problems difficult, and I suppose no one really likes to wrestle with them. Any help will be appreciated.
If you don't have an answer, but you have a good idea where I might find one, it would be appreciated.


OK. I don't have a complete answer. But I downloaded Adobe Reader, and it prints. It may not solve all problems, but I think I like it for pdf's better than Document Viewer anyway.

---

