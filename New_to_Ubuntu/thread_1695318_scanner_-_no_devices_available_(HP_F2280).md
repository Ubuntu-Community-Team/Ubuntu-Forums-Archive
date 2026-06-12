---
title: "scanner - no devices available (HP F2280)"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by col48 on 2011-02-25
I'm not sure what caused it to happen but my MFP is no longer available to xsane as a scanner after over a year of running fine.  I've looked at many threads already and come to a blank wall.  There needs to be a checklist somewhere....

The printing function works fine, although Colour printing stopped working at the same time as the scanner.  Black+White carried on OK.  Cured Colour by designating a "new" printer.  But xsane continues with the same story. ("no devices available")

OS: Hardy
MFP: HP Deskjet F2280

sane-find-scanner reports
```
found USB scanner (vendor=0x03f0 [HP], product=0x2404 [Deskjet F2200 series]) at libusb:001:006

``` 
but scanimage does not find the scanner, nor do sane or xsane.
It makes no difference whether or not I run using sudo or gksudo.

lsusb
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 03f0:2404 Hewlett-Packard 
Bus 001 Device 005: ID 0803:3095 Zoom Telephonics, Inc. 
Bus 001 Device 004: ID 059b:0031 Iomega Corp. Zip 100 (Type 3)
Bus 001 Device 003: ID 15ca:00c3  
Bus 001 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 0000:0000  

```

dir -l in /dev/bus/usb/001$:
```
crw-rw-rw-  1 root vboxusers 189, 0 2011-02-25 22:41 001
crw-rw-rw-  1 root vboxusers 189, 1 2011-02-25 22:41 002
crw-rw-rw-  1 root vboxusers 189, 2 2011-02-25 22:41 003
crw-rw-rw-  1 root vboxusers 189, 3 2011-02-25 22:41 004
crw-rw-rw-  1 root vboxusers 189, 4 2011-02-25 22:41 005
crw-rw----+ 1 root lp        189, 5 2011-02-25 22:44 006

```

My user is in the lp, lpadmin, saned and scanner groups.

There must be something simple....
Anyone know what it is?

---

### Post by col48 on 2011-02-26
Anyone?  Aka... bump.

---

### Post by Spyderkid on 2011-02-26
[http://ubuntuforums.org/showthread.php?t=905287](http://ubuntuforums.org/showthread.php?t=905287)


look there^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

---

### Post by Spyderkid on 2011-02-26
[http://www.google.co.uk/url?sa=t&source=web&cd=14&ved=0CCoQFjADOAo&url=http%3A%2F%2Fwww.linux-drivers.org%2F&ei=SjtpTc6VIIKLhQetnZXsDg&usg=AFQjCNF0-2a7BKBQjWDNhyTXryNXRGtkLQ](http://www.google.co.uk/url?sa=t&source=web&cd=14&ved=0CCoQFjADOAo&url=http%3A%2F%2Fwww.linux-drivers.org%2F&ei=SjtpTc6VIIKLhQetnZXsDg&usg=AFQjCNF0-2a7BKBQjWDNhyTXryNXRGtkLQ)


and there^^^^^^^^^^

---

### Post by Spyderkid on 2011-02-26
also update to 10.04 (the long term realese)?

---

### Post by col48 on 2011-02-26
Thanks Spyderkid.

Now I know what I had to do, which was reinstall hpoj (as per my 2009 post which you kindly pointed me to!).  This not only got the scanner in touch again, but it swapped round two logical printers (both pointing to the same device) - previously A was working and B not, now B works and A does not.  No problem as I had created A to replace B in any case when B stopped working.

I wonder how hpoj got deinstalled?  I don't tidy up much in that way usually.  Hmm.

As for 10.04, I am getting there!

---

### Post by col48 on 2011-02-27
Now that I have got everything running, here is a checklist which might help other people, even if they have not got an HP F2280 printer/scanner.

My OS is Hardy 8.04 and this checklist may not apply to other OS.

[B]Warning:
[/B]I am no expert in what is needed, but the items listed are based on what has been suggested as needing checking in various threads and web pages.  So some of these things may be overkill or irrelevant and there may be other things which are needed which I have not listed.

[B]My setup
[/B]I have one physical HP F2280 which has two logical printers:
Deskjet_F2200_series is the original which is used for Black & White only
Deskjet_F2200_0906 was added later to do Colour printing.

Having the two is a simple way of switching between Colour and Black without checking and perhaps changing properties for every print.

The F2280 is currently plugged into usb bus 1 port(?) 6.

**The checklist** (there is no significance in the order of this list)

NB the syntax of the rules files can mean that rows which are present may not be applied, as there can be conditional GOTOs, so be careful.  In my case all the lines shown here are applied.

/etc/udev/rules.d/40-permissions-rules
includes the line
```
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",	GROUP="lp"
```
/etc/udev/rules.d/40-basic-permissions-rules
includes the lines (together and in this order)
```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device",		MODE="0666"
```
/etc/udev/rules.d/55-hpmud-rules
includes the line
```
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??04", OWNER="root", GROUP="lp", MODE="660"
```
The F2280 is Vendor 03f0 product 2404.

/etc/sane.d/dll.conf
includes the line (in my case at the end when the rest of the file is in alphabetical order)
```
hpaio
```
output of scanimage -L
```
device `hpoj:mlc:usb:Deskjet_F2200_series' is a HP Deskjet F2200 series multi-function peripheral
```
packages installed include
```
hplip
hplip-data 
hplip-doc
hpoj
hpoj-xojpanel
```
Synaptic says hplip and friends are version 2.8.2-0ubuntu8.2 which is the latest available in the Hardy repositories.  Somewhere I read that I need 2.8.6 or later for scanning to work and because of this I in fact have 3.10.2 from Sourceforge (as reported by hp-check)

hpoj is version 0.91-13 from the Hardy repository

hp-check claims that hplip and hpoj are not compatible, but I seem to need both installed to have both print and scan available.

output of hp-check (in its logfile)
```
Initializing. Please wait...
Ubuntu


8.04


scheduler is running


1.3.7


Linux col48-desktop 2.6.24-28-generic #1 SMP Fri Feb 11 17:36:45 UTC 2011 i686 GNU/Linux


hp-check[7641]: info: :
hp-check[7641]: info: :---------------
hp-check[7641]: info: :| SYSTEM INFO |
hp-check[7641]: info: :---------------
hp-check[7641]: info: :
hp-check[7641]: info: :[01mBasic system information:[0m
hp-check[7641]: info: :Linux col48-desktop 2.6.24-28-generic #1 SMP Fri Feb 11 17:36:45 UTC 2011 i686 GNU/Linux

hp-check[7641]: info: :
hp-check[7641]: info: :[01mDistribution:[0m
hp-check[7641]: info: :ubuntu 8.04
hp-check[7641]: info: :[01m
HPOJ running?[0m
error: Yes, HPOJ is running. HPLIP is not compatible with HPOJ. To run HPLIP, please remove HPOJ.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking Python version...[0m
hp-check[7641]: info: :OK, version 2.5.2 installed
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking PyQt version...[0m
hp-check[7641]: info: :OK, version 3.17 installed.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking SIP version...[0m
error: SIP not installed or version not found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for CUPS...[0m
hp-check[7641]: info: :Status: scheduler is running
hp-check[7641]: info: :Version: 1.3.7
hp-check[7641]: info: :
hp-check[7641]: info: :
hp-check[7641]: info: :------------------------------------
hp-check[7641]: info: :| COMPILE AND RUNTIME DEPENDENCIES |
hp-check[7641]: info: :------------------------------------
hp-check[7641]: info: :
note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: cups - Common Unix Printing System...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: cups-ddk - CUPS driver development kit...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: cups-devel- Common Unix Printing System development files...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: gcc - GNU Project C and C++ Compiler...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: libcrypto - OpenSSL cryptographic library...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: libjpeg - JPEG library...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: libnetsnmp-devel - SNMP networking library development files...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: libpthread - POSIX threads library...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: libtool - Library building support services...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: libusb - USB library...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: make - GNU make utility to maintain groups of programs...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: ppdev - Parallel port support kernel module....[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: PyQt - Qt interface for Python...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: python-devel - Python development files...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: Python 2.3 or greater - Required for fax functionality...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: Python 2.2 or greater - Python programming language...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: Reportlab - PDF library for Python...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: SANE - Scanning library...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: SANE - Scanning library development files...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: scanimage - Shell scanning program...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for dependency: xsane - Graphical scanner frontend for SANE...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :
hp-check[7641]: info: :----------------------
hp-check[7641]: info: :| HPLIP INSTALLATION |
hp-check[7641]: info: :----------------------
hp-check[7641]: info: :
hp-check[7641]: info: :
hp-check[7641]: info: :[01mCurrently installed HPLIP version...[0m
hp-check[7641]: info: :HPLIP 3.10.2 currently installed in '/usr/share/hplip'.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mCurrent contents of '/etc/hp/hplip.conf' file:[0m
hp-check[7641]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-3.10.2
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

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
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=no
cups-ppd-install=yes
internal-tag=3.10.2rc1.9
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=no
hpcups-only-build=no
hpijs-only-build=no

hp-check[7641]: info: :
hp-check[7641]: info: :--------------------------
hp-check[7641]: info: :| DISCOVERED USB DEVICES |
hp-check[7641]: info: :--------------------------
hp-check[7641]: info: :
hp-check[7641]: info: :No devices found.
hp-check[7641]: info: :
hp-check[7641]: info: :---------------------------------
hp-check[7641]: info: :| INSTALLED CUPS PRINTER QUEUES |
hp-check[7641]: info: :---------------------------------
hp-check[7641]: info: :
hp-check[7641]: info: :
hp-check[7641]: info: :[01mDeskjet_F2200_0906[0m
hp-check[7641]: info: :[01m------------------[0m
hp-check[7641]: info: :Type: Printer
hp-check[7641]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[7641]: info: :Device URI: hp:/usb/Deskjet_F2200_series?serial=CN8844T2VK0534
hp-check[7641]: info: :PPD: /etc/cups/ppd/Deskjet_F2200_0906.ppd
hp-check[7641]: info: :PPD Description: HP Deskjet f2200 Series hpijs, hpijs 3.9.2
hp-check[7641]: info: :Printer status: printer Deskjet_F2200_0906 is idle.  enabled since Sat 26 Feb 2011 19:48:26 GMT

error: Unsupported model: Deskjet_F2200_series
hp-check[7641]: info: :
hp-check[7641]: info: :[01mDeskjet_F2200_series[0m
hp-check[7641]: info: :[01m--------------------[0m
hp-check[7641]: info: :Type: Printer
hp-check[7641]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[7641]: info: :Device URI: hp:/usb/Deskjet_F2200_series?serial=CN8844T2VK0534
hp-check[7641]: info: :PPD: /etc/cups/ppd/Deskjet_F2200_series.ppd
hp-check[7641]: info: :PPD Description: HP DeskJet F2100 Foomatic/hpijs, hpijs 2.8.2
hp-check[7641]: info: :Printer status: printer Deskjet_F2200_series is idle.  enabled since Sat 26 Feb 2011 19:46:54 GMT

error: Unsupported model: Deskjet_F2200_series
hp-check[7641]: info: :
hp-check[7641]: info: :[01mPDF[0m
hp-check[7641]: info: :[01m---[0m
hp-check[7641]: info: :Type: Unknown
hp-check[7641]: info: :Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
hp-check[7641]: info: :Device URI: cups-pdf:/
hp-check[7641]: info: :PPD: /etc/cups/ppd/PDF.ppd
hp-check[7641]: info: :PPD Description: Generic PDF file generator
hp-check[7641]: info: :Printer status: printer PDF is idle.  enabled since Thu 01 Jan 2009 11:44:14 GMT

warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
hp-check[7641]: info: :
hp-check[7641]: info: :----------------------
hp-check[7641]: info: :| SANE CONFIGURATION |
hp-check[7641]: info: :----------------------
hp-check[7641]: info: :
hp-check[7641]: info: :[01m'hpaio' in '/etc/sane.d/dll.conf'...[0m
hp-check[7641]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking output of 'scanimage -L'...[0m
hp-check[7641]: info: :device `hpoj:mlc:usb:Deskjet_F2200_series' is a HP Deskjet F2200 series multi-function peripheral


hp-check[7641]: info: :
hp-check[7641]: info: :---------------------
hp-check[7641]: info: :| PYTHON EXTENSIONS |
hp-check[7641]: info: :---------------------
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking 'cupsext' CUPS extension...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking 'pcardext' Photocard extension...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking 'hpmudext' I/O extension...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking 'scanext' SANE scanning extension...[0m
hp-check[7641]: info: :OK, found.
hp-check[7641]: info: :
hp-check[7641]: info: :
hp-check[7641]: info: :-----------------
hp-check[7641]: info: :| USB I/O SETUP |
hp-check[7641]: info: :-----------------
hp-check[7641]: info: :
hp-check[7641]: info: :
hp-check[7641]: info: :[01mChecking for permissions of USB attached printers...[0m
hp-check[7641]: info: :
HP Device 0x2404 at 001:006: 
hp-check[7641]: info: :    Device URI: hp:/usb/Deskjet_F2200_series?serial=CN8844T2VK0534
hp-check[7641]: info: :    Device node: /dev/bus/usb/001/006
hp-check[7641]: info: :    Mode: 0660
hp-check[7641]: info: :getfacl: Removing leading '/' from absolute path names

# file: dev/bus/usb/001/006

# owner: root

# group: lp

user::rw-

user:col48:rw-

group::rw-

mask::rw-

other::---




hp-check[7641]: info: :
hp-check[7641]: info: :-----------
hp-check[7641]: info: :| SUMMARY |
hp-check[7641]: info: :-----------
hp-check[7641]: info: :
error: 5 errors and/or warnings.
hp-check[7641]: info: :
hp-check[7641]: info: :Please refer to the installation instructions at:
hp-check[7641]: info: :http://hplip.sourceforge.net/install/index.html

```

---

### Post by Spyderkid on 2011-02-27
glad I could be of help

(i still reccomend to update to Lucid 10.04)

---

### Post by col48 on 2011-03-02
Post #7 contains my checklist for Ubuntu 8.04 Hardy Heron.

This checklist may help any Ubuntu 10.04 Lucid Lynx user in the same boat.  I have now installed Lucid to dual-boot alongside Hardy. 

[B]Warning
[/B]This list is based on the same checks which inspired the list for Hardy.  So it is likely that some things here are irrelevant and quite possible that other things which are needed have been omitted. I repeat, I am no expert.

**My Setup**
I have one physical HP F2280 which is set up at the moment for either Black & White or Colour.

The F2280 is currently plugged into usb bus 1 port(?) 6.

**The checklist** (there is no significance in the order of this list)

NB the syntax of the rules files can mean that rows which are present may not be applied, as there can be conditional GOTOs, so be careful. In my case the lines shown here are applied.

/lib/udev/rules.d/40-hplip-rules     (NB not /etc/...)
includes the lines
```
# Check for Deskjet products (0x03f0xx04).
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="??04", GROUP="lp", ENV{ID_HPLIP}="1"

```/lib/udev/rules.d/55-hpmud-rules
/lib/udev/rules/40-libsane-rules
do not include any lines which look relevant

/etc/sane.d/dll.conf
does not include any reference to hpaio

output of scanimage -L
```
device `hpaio:/usb/Deskjet_F2200_series?serial=CN8844T2VK0534' is a Hewlett-Packard Deskjet_F2200_series all-in-one

```

packages installed include
```
hplip
hplip-data 
hplip-doc

```
but _not_ hpoj.

Synaptic and hp-check agree that hplip and friends are version 3.10.2-2ubuntu2.2 which is the latest available in the Lucid repositories. 

output of hp-check in its log file
```
hp-check[2925]: info: :
Initializing. Please wait...
Ubuntu


10.04


scheduler is running


1.4.3


Linux col48-desktop 2.6.32-28-generic-pae #55-Ubuntu SMP Mon Jan 10 22:34:08 UTC 2011 i686 GNU/Linux


hp-check[2925]: info: :
hp-check[2925]: info: :---------------
hp-check[2925]: info: :| SYSTEM INFO |
hp-check[2925]: info: :---------------
hp-check[2925]: info: :
hp-check[2925]: info: :[01mBasic system information:[0m
hp-check[2925]: info: :Linux col48-desktop 2.6.32-28-generic-pae #55-Ubuntu SMP Mon Jan 10 22:34:08 UTC 2011 i686 GNU/Linux

hp-check[2925]: info: :
hp-check[2925]: info: :[01mDistribution:[0m
hp-check[2925]: info: :ubuntu 10.04
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking Python version...[0m
hp-check[2925]: info: :OK, version 2.6.5 installed
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking PyQt 4.x version...[0m
error: NOT FOUND OR FAILED TO LOAD!
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for CUPS...[0m
hp-check[2925]: info: :Status: scheduler is running
hp-check[2925]: info: :Version: 1.4.3
hp-check[2925]: info: :error_log is set to level: warn
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dbus/python-dbus...[0m
hp-check[2925]: info: :dbus daemon is running.
hp-check[2925]: info: :python-dbus version: 0.83.0
hp-check[2925]: info: :
hp-check[2925]: info: :
hp-check[2925]: info: :------------------------------------
hp-check[2925]: info: :| COMPILE AND RUNTIME DEPENDENCIES |
hp-check[2925]: info: :------------------------------------
hp-check[2925]: info: :
note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: CUPS - Common Unix Printing System...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: CUPS devel- Common Unix Printing System development files...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: CUPS image - CUPS image development files...[0m
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes libcupsimage2-dev
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: DBus - Message bus system...[0m
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes libdbus-1-dev
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: gcc - GNU Project C and C++ Compiler...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: libcrypto - OpenSSL cryptographic library...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: libjpeg - JPEG library...[0m
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes libjpeg62-dev
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: libnetsnmp-devel - SNMP networking library development files...[0m
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes libsnmp-dev
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: libpthread - POSIX threads library...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: libtool - Library building support services...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: libusb - USB library...[0m
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes libusb-dev
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: make - GNU make utility to maintain groups of programs...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: PolicyKit - Administrative policy framework...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: PyQt 4 DBus - DBus Support for PyQt4...[0m
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes python-qt4-dbus
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: Python DBus - Python bindings for DBus...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: Python devel - Python development files...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: Python XML libraries...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: Python 2.3 or greater - Required for fax functionality...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: Python 2.2 or greater - Python programming language...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: Reportlab - PDF library for Python...[0m
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes python-reportlab
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: SANE - Scanning library...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: SANE - Scanning library development files...[0m
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[2925]: info: :To install this dependency, execute this command:
hp-check[2925]: info: :sudo aptitude install --assume-yes libsane-dev
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: scanimage - Shell scanning program...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for dependency: xsane - Graphical scanner frontend for SANE...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :
hp-check[2925]: info: :----------------------
hp-check[2925]: info: :| HPLIP INSTALLATION |
hp-check[2925]: info: :----------------------
hp-check[2925]: info: :
hp-check[2925]: info: :
hp-check[2925]: info: :[01mCurrently installed HPLIP version...[0m
hp-check[2925]: info: :HPLIP 3.10.2 currently installed in '/usr/share/hplip'.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mCurrent contents of '/etc/hp/hplip.conf' file:[0m
hp-check[2925]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

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
internal-tag=3.10.2rc1.9
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

hp-check[2925]: info: :
hp-check[2925]: info: :[01mCurrent contents of '/var/lib/hp/hplip.state' file:[0m
hp-check[2925]: info: :# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0


hp-check[2925]: info: :
hp-check[2925]: info: :[01mCurrent contents of '~/.hplip/hplip.conf' file:[0m
hp-check[2925]: info: :[installation]
date_time = 02/03/11 12:29:41
version = 3.10.2rc1.9


hp-check[2925]: info: :
hp-check[2925]: info: :--------------------------
hp-check[2925]: info: :| DISCOVERED USB DEVICES |
hp-check[2925]: info: :--------------------------
hp-check[2925]: info: :
hp-check[2925]: info: :  Device URI                        Model                  
hp-check[2925]: info: :  --------------------------------  -----------------------
hp-check[2925]: info: :  hp:/usb/Deskjet_F2200_series?ser  HP Deskjet F2200 series
  ial=CN8844T2VK0534                                       
hp-check[2925]: info: :
hp-check[2925]: info: :---------------------------------
hp-check[2925]: info: :| INSTALLED CUPS PRINTER QUEUES |
hp-check[2925]: info: :---------------------------------
hp-check[2925]: info: :
hp-check[2925]: info: :
hp-check[2925]: info: :[01mDeskjet-F2200-series[0m
hp-check[2925]: info: :[01m--------------------[0m
hp-check[2925]: info: :Type: Printer
hp-check[2925]: info: :Device URI: hp:/usb/Deskjet_F2200_series?serial=CN8844T2VK0534
hp-check[2925]: info: :PPD: /etc/cups/ppd/Deskjet-F2200-series.ppd
hp-check[2925]: info: :PPD Description: HP Deskjet f2200 Series hpijs, 3.10.2
hp-check[2925]: info: :Printer status: printer Deskjet-F2200-series is idle.  enabled since Thu 24 Feb 2011 19:08:50 GMT

warning: Unable to connect to dbus. Is hp-systray running?
hp-check[2925]: info: :Communication status: Good
hp-check[2925]: info: :
hp-check[2925]: info: :
hp-check[2925]: info: :----------------------
hp-check[2925]: info: :| SANE CONFIGURATION |
hp-check[2925]: info: :----------------------
hp-check[2925]: info: :
hp-check[2925]: info: :[01m'hpaio' in '/etc/sane.d/dll.conf'...[0m
hp-check[2925]: info: :[01m'hpaio' in '/etc/sane.d/dll.d/hplip'...[0m
hp-check[2925]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking output of 'scanimage -L'...[0m
hp-check[2925]: info: :device `hpaio:/usb/Deskjet_F2200_series?serial=CN8844T2VK0534' is a Hewlett-Packard Deskjet_F2200_series all-in-one


hp-check[2925]: info: :
hp-check[2925]: info: :---------------------
hp-check[2925]: info: :| PYTHON EXTENSIONS |
hp-check[2925]: info: :---------------------
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking 'cupsext' CUPS extension...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking 'pcardext' Photocard extension...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking 'hpmudext' I/O extension...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking 'scanext' SANE scanning extension...[0m
hp-check[2925]: info: :OK, found.
hp-check[2925]: info: :
hp-check[2925]: info: :
hp-check[2925]: info: :
hp-check[2925]: info: :-----------------
hp-check[2925]: info: :| USB I/O SETUP |
hp-check[2925]: info: :-----------------
hp-check[2925]: info: :
hp-check[2925]: info: :[01mChecking for permissions of USB attached printers...[0m
hp-check[2925]: info: :
HP Device 0x2404 at 002:006: 
hp-check[2925]: info: :    Device URI: hp:/usb/Deskjet_F2200_series?serial=CN8844T2VK0534
warning: Unable to connect to dbus. Is hp-systray running?
hp-check[2925]: info: :    Device node: /dev/bus/usb/002/006
hp-check[2925]: info: :    Mode: 0664
hp-check[2925]: info: :getfacl: Removing leading '/' from absolute path names

# file: dev/bus/usb/002/006

# owner: root

# group: lp

user::rw-

user:col48:rw-

group::rw-

mask::rw-

other::r--




hp-check[2925]: info: :
hp-check[2925]: info: :---------------
hp-check[2925]: info: :| USER GROUPS |
hp-check[2925]: info: :---------------
hp-check[2925]: info: :
hp-check[2925]: info: :col48 adm dialout cdrom plugdev lpadmin admin sambashare


error: User needs to be member of group 'lp' to enable print, scan & fax.
hp-check[2925]: info: :[32;01mUser member of group 'lpadmin'.[0m
hp-check[2925]: info: :
hp-check[2925]: info: :-----------
hp-check[2925]: info: :| SUMMARY |
hp-check[2925]: info: :-----------
hp-check[2925]: info: :
error: 9 errors and/or warnings.
hp-check[2925]: info: :
hp-check[2925]: info: :[01mSummary of needed commands to run to satisfy missing dependencies:[0m
hp-check[2925]: info: :sudo aptitude install --assume-yes libcupsimage2-dev
hp-check[2925]: info: :sudo aptitude install --assume-yes libdbus-1-dev
hp-check[2925]: info: :sudo aptitude install --assume-yes libjpeg62-dev
hp-check[2925]: info: :sudo aptitude install --assume-yes libsnmp-dev
hp-check[2925]: info: :sudo aptitude install --assume-yes libusb-dev
hp-check[2925]: info: :sudo aptitude install --assume-yes python-qt4-dbus
hp-check[2925]: info: :sudo aptitude install --assume-yes python-reportlab
hp-check[2925]: info: :sudo aptitude install --assume-yes libsane-dev
hp-check[2925]: info: :
hp-check[2925]: info: :Please refer to the installation instructions at:
hp-check[2925]: info: :http://hplip.sourceforge.net/install/index.html

hp-check[2925]: info: :
hp-check[2925]: info: :Done.
```Note that I am not a member of the lp group and the missing dependencies look from their names to be developer's needs rather than user's needs.  I can still print and scan without any of it.

---

