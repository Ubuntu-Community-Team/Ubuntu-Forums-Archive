---
title: "Printer Connection Problems"
date: 2015-04-15
forum: Networking &amp; Wireless
---

### Post by Stephen_Revere on 2015-04-15
Hi, I'm running Ubuntu 12.04, and my printer is an HP Office Jet Pro 8600

I got the following return on my sudo hp-check -r:
[INDENT]HP Linux Imaging and Printing System (ver. 3.12.2)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2011-14 Hewlett-Packard Development Company, LP
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
Linux steve-Inspiron-3421 3.2.0-80-generic #116-Ubuntu SMP Mon Mar 23 17:11:03 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Distribution:
ubuntu 12.04

Checking Python version...
OK, version 2.7.3 installed

Checking PyQt 4.x version...
OK, version 4.9.1 installed.

Checking for CUPS...
Status: scheduler is running
warning: Version: (cups-config) Not available. Unable to determine installed version of CUPS.)
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 1.0.0

------------------------
| RUNTIME DEPENDENCIES |
------------------------

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

----------------------
| HPLIP INSTALLATION |
----------------------
Currently installed HPLIP version...
HPLIP 3.12.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.2

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
internal-tag=3.12.2
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no

Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0

Current contents of '~/.hplip/hplip.conf' file:
[last_used]
device_uri = hpfax:/net/Officejet_Pro_8600?ip=192.168.10.132

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

HP-Officejet-Pro-8600-2
-----------------------
Type: Printer
Device URI: hp:/net/Officejet_Pro_8600?ip=192.168.10.132
PPD: /etc/cups/ppd/HP-Officejet-Pro-8600-2.ppd
PPD Description: HP Officejet Pro 8600, hpcups 3.12.2
Printer status: printer HP-Officejet-Pro-8600-2 is idle.  enabled since Wed 15 Apr 2015 /usr/lib/cups/backend/hp failed
[B]error: Unable to communicate with device (code=12): hp:/net/Officejet_Pro_8600?ip=192.168.10.132
error: unable to open channel
error: Communication status: Failed
[/B]----------------------
| SANE CONFIGURATION |
----------------------
'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/net/Officejet_Pro_8600?ip=192.168.10.132' is a Hewlett-Packard Officejet_Pro_8600 all-in-one
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
---------------
| USER GROUPS |
---------------
root
[B]error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.[/B]
-----------
| SUMMARY |
-----------
[B]error: 3 errors and/or warnings.
[/B]
Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.

[/INDENT]
Can anyone tell me what to do next?

---

### Post by michi1983 on 2015-04-15
Can you ping the IP address of the printer (192.168.10.132) from your machine? Are you on the same subnet? 
What does ```
sudo ifconfig
``` say?

---

