---
title: "Simple Scanner not working?"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Georgia boy on 2010-07-05
Hi. After finally getting my printer back to working again, just checked and it is printing, I can't seem to scan using Simple Scanner again. I had used it before. I like it because of it being simple to use. But for some reason it's down the tubes. Has someone else been having problems also with Simple Scanner? Ideas anyone? I'm including a screenshot of the error. Help?

---

### Post by Georgia boy on 2010-07-05
Just did a removal/re-installation of Simple Scan. Still same thing. Even removed USB and reinstalled. Trying to do XSANE download and try it out. Well, so much for that idea. Didn't work either. Included screen shot for it as well. Ideas as to why I'm getting these problems? Turned printer off and on several times, unplugged and replugged USB cable in the computer. Still getting the same thing with both Simple Scan and XSANE. As I said in previous post Simple Scan was working before. Is something going on with these?

Tom

---

### Post by Georgia boy on 2010-07-06
Removed and reinstalled scanner again. Powered off Printer, pulled USB cable, reinstalled, powered all again. Scanner will recognize the printer. Printed blank page, however still won't recognize the scanner portion. XSANE still the same. Ideas anyone?

Thanks

Tom

---

### Post by Morbius1 on 2010-07-06
Take a look at the ownership / permissions of the .sane directory of your home folder and see if you are the owner. For example:
```
ls -al /home/morbius/.sane
```

---

### Post by Georgia boy on 2010-07-06
Here's what I got when I did that in terminal:

thomas@thomas-desktop:~$ ls -al /home/thomas/.sane
total 12
drwxrwx---  3 thomas thomas 4096 2010-07-05 19:21 .
drwxr-xr-x 54 thomas thomas 4096 2010-07-06 05:41 ..
drwxrwx---  2 thomas thomas 4096 2010-07-05 19:21 xsane
thomas@thomas-desktop:~$ 

Did I do this right? Can't make heads or tails out of this.

Tom

---

### Post by philinux on 2010-07-06
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

[https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)

---

### Post by Georgia boy on 2010-07-06
Did this: sudo apt-get install libsane-extras

Then tried doing this:   1. Edit the /etc/sane.d/dll.conf and enable the right driver for your scanner. Look for the lines that say: 

# The following backends are not part of the SANE distribution
# but are provided by the libsane-extras Debian package

Was using the first when I got that information. Still don't work. I know that the model I'm using is old but it still prints after I got it going again. Was scanning but for some reason it stopped. Can't get it to start scanning again. 

Tom

---

### Post by lidex on 2010-07-07
What is the output of```
 lsusb
```
Did you check the links *philinux* posted?

---

### Post by Georgia boy on 2010-07-07
> **lidex said:**
> What is the output of```
 lsusb
```
Did you check the links *philinux* posted?



thomas@thomas-desktop:~$ lsusb
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
thomas@thomas-desktop:~$ 


 I checked the two links out that Philinux mentioned. That is where the information came from in my last reply.
When I tried the ETC/Sane part I was being told I wasn't authorized to do so.
Thanks

Tom

---

### Post by lidex on 2010-07-07
I'm not seeing the scanner or the printer on your usb ports. Is it turned on?

---

### Post by Georgia boy on 2010-07-07
My Bad. Mind was still asleep. Thought it was on. Didn't pay attention. Here are the new readings:
thomas@thomas-desktop:~$  lsusb
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:1411 Hewlett-Packard PSC 750
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
thomas@thomas-desktop:~$ 

Sorry about that. Hope this makes better sense. As you can see it's an all in one except for no faxing since I don't need faxing.

Thanks

Tom

---

### Post by Irony on 2010-07-07
Have you tried deleting the following folder;
```

~/.sane
```

---

### Post by Georgia boy on 2010-07-07
I did a complete removal and reinstall of Simple scan from the software manager when I first started having the problem. Same thing or do I need to go and do that in terminal? Plus if I do that then what will I do to bring back?

Thanks

Tom

---

### Post by philinux on 2010-07-07
> **Georgia boy said:**
> I did a complete removal and reinstall of Simple scan from the software manager when I first started having the problem. Same thing or do I need to go and do that in terminal? Plus if I do that then what will I do to bring back?

Thanks

Tom

That folder is just a config file folder. It will get re-created when use use sane etc. Same with all config folders. Except like firefox you would loose you bookmarks and with gconf you would loose any customisation.

---

### Post by Georgia boy on 2010-07-07
> **philinux said:**
> That folder is just a config file folder. It will get re-created when use use sane etc. Same with all config folders. Except like firefox you would loose you bookmarks and with gconf you would loose any customisation.

Tried this ~/.sane in terminal. Said that it's a directory. Wouldn't let me do anything with it. Found two sane folders when doing a search in home but can't do anything with them either. What gives?

Thanks

Tom

---

### Post by philinux on 2010-07-07
Places>Home Folder press ctrl h to reveal the hidden .folders

---

### Post by Georgia boy on 2010-07-07
Did the removal of the folder. Removed also Simple Scan. Rebooted machine. Reinstalled Simple Scan. Same thing happening. Just don't want to recognize the scanner part of the printer for some reason. Due to the updates that came out since last week? 
Was working last week. Then started having trouble with the printer. Got it back now scanner portion acting up.

Thanks

Tom

---

### Post by Georgia boy on 2010-07-08
Any new ideas to try out or am I looking at having to get a new printer/scanner/copier?

Thanks

Tom

---

### Post by philinux on 2010-07-08
Have you got the hplip-gui and the latest hplip version installed?

It is an HP machine I guess from lsusb output.

---

### Post by Georgia boy on 2010-07-08
As far as I can tell I do.

---

### Post by philinux on 2010-07-08
Does the blue HP icon show up top right and can you use it to see if it reports on the scanner?

---

### Post by Georgia boy on 2010-07-08
No  Blue HP Icon at top of panel.

---

### Post by philinux on 2010-07-08
> **Georgia boy said:**
> No  Blue HP Icon at top of panel.

Fire it up then from the menu. Cant remember where it lives.

---

### Post by Georgia boy on 2010-07-08
Don't know if this will help or not, but did a printer test page and shows that make and model is HP PSC 750 hpijs, 3.10.2. Driver name hp-psc_750-hpijs.ppd, driver version is hpijs 3.10.2. Prints fine, wonder if having scanner because of the not being supported any longer or because of latest updates? But, if not supported wouldn't the printer also quit totally and wouldn't work no matter what we did? Not just scanner?


Tom

---

### Post by Georgia boy on 2010-07-08
Fired up. But not finding printer for some reason. Have to go to work. Will try in morning again. Printer works but the HP don't recognize it.

Tom

---

### Post by lidex on 2010-07-08
This may help:
[http://www.openprinting.org/printer/HP/HP-PSC_750]("http://www.openprinting.org/printer/HP/HP-PSC_750")

---

### Post by Georgia boy on 2010-07-09
Thanks Lidex. Went to that site. Tried to do a download of HPLIP 3.10.2.
Was told that Ubuntu has that and supports the printer. How can I make sure that it is up and running or not? I've got so many things going that I'm having trouble keeping up with it all. 
Went to Synaptic Package Monitor and I pasted in search. I see where there is a green block beside it. Does that mean it's installed? Should I mark for re-installation or anything?
Have a wonderful weekend!!

Thanks

Tom

---

### Post by philinux on 2010-07-09
> apt-cache policy hplip
hplip:
  Installed: 3.10.2-2ubuntu2
  Candidate: 3.10.2-2ubuntu2


That's installed by default in 10.04

Have you installed hplip-gui

---

### Post by Georgia boy on 2010-07-09
Did a screen shot. It shows a different model in there. How do I go about changing to the model I have? I wonder if this might be part of the problem I'm having.

Tom

---

### Post by philinux on 2010-07-09
> **Georgia boy said:**
> Did a screen shot. It shows a different model in there. How do I go about changing to the model I have? I wonder if this might be part of the problem I'm having.

Tom

Well yes having the right model selected would help.

---

### Post by Georgia boy on 2010-07-09
Didn't know that the thing had set up like that. Could you advise me as how to go about changing to correct model? I won't be able to do so now but will be able to tomorrow. Still learning as you can tell. Found out by accident when I looked in the package about the version and made it show a screen of what was going on. So, how do I go about getting that mess straightened out?

Have a great day and a wonderful weekend!!

Thanks

Tom

---

### Post by lidex on 2010-07-09
[http://www.google.com/search?q=HP+PSC+750&sitesearch=ubuntuforums.org]("http://www.google.com/search?q=HP+PSC+750&sitesearch=ubuntuforums.org")

---

### Post by Georgia boy on 2010-07-10
Thanks for the links. Read through them but didn't see any help in them. The screen shot I took while in the packages on HLIP. Was that actually the one being shown for my printer or is it just a sample that they were using? If it is really being shown as what I have installed how do I go about getting the right printer model to be shown? In the printer section under Administration I show the HP PSC 750. But am confused if what is showing in HLIP is the other model. As I mentioned when in Synaptic I clicked on HLIP and clicked the screen shot button and the other model is what showed. So, don't know if it's just a generic picture or is actually what they think I have for a printer. If so, how do I get the right printer in HLIP? Do I remove HLIP somehow and reinstall it? How? Also, should the printer be on during all of this? 

Sorry but just don't know what's going on with this thing any more.

On the Printer Test Page it shows printer name and description as Hewlett-Packard PSC 750.  Make and model: HP PSC 750 hpijs, 3.10.2, Driver name; ph-psc 750-hpijs.ppd, Driver version: hpijs 3.10.2. 
So, what can I do to get the scanner back to working. Printer works fine in printing mode.
Thanks

Tom

---

### Post by lidex on 2010-07-10
You lost me.
[http://hplipopensource.com/hplip-web/models/psc/psc_750.html#note1]("http://hplipopensource.com/hplip-web/models/psc/psc_750.html#note1")
[http://www.openprinting.org/driver/hplip]("http://www.openprinting.org/driver/hplip")
[http://www.openprinting.org/printer/HP/HP-PSC_750]("http://www.openprinting.org/printer/HP/HP-PSC_750")

---

### Post by Georgia boy on 2010-07-10
Ran this in terminal: dpkg -l hplip
Got the following:


thomas@thomas-desktop:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          3.10.2-2ubuntu HP Linux Printing and Imaging System (HPLIP)
thomas@thomas-desktop:~$ 

According to the next statement I have the hplip already installed.

If you see "ii" in the first column before "hplip", then HPLIP is already installed. If you want to use the currently installed version of HPLIP, try running hp-setup in a terminal shell.

So, how do I get the hp-setup done in the terminal shell to make sure it's working? Or, is there something I can put into terminal to see if it's already active?

Tom

---

### Post by Georgia boy on 2010-07-10
Okay,figured out how to do the install through shell.  Did this:

thomas@thomas-desktop:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
Searching... (bus=usb, search=(None), desc=0)
/
Done.
thomas@thomas-desktop:~$ 


However with the url:  hp:/usb/PSC_750?serial=MY2AED40PTWB nothing at all happens. With the other way I have installed with the url:  usb://HP/PSC%20750?serial=MY2AED40PTWB I can print, just can't scan. So, why when doing the install the way I did through terminal it's just sitting there doing nothing, but when using the way I had set up by just adding printer and clicking apply when I saw the USB it prints but don't scan? 

Don't make any sense at all.

Sorry if sounds like ranting, just confused.

Tom

---

### Post by lidex on 2010-07-10
Give this a run-through:
[https://help.ubuntu.com/community/HpAllInOne]("https://help.ubuntu.com/community/HpAllInOne")


[http://www.linuxquestions.org/questions/linux-hardware-18/hp-psc-1110-scanner-not-found-793640/]("http://www.linuxquestions.org/questions/linux-hardware-18/hp-psc-1110-scanner-not-found-793640/")
[http://ubuntuforums.org/showthread.php?t=70531]("http://ubuntuforums.org/showthread.php?t=70531")

---

### Post by Georgia boy on 2010-07-10
On the first link followed did the hp-check and got this:
thomas@thomas-desktop:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.10.2)
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
Linux thomas-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
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

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsimage2-dev

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes build-essential

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

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
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

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


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
working_dir = .
device_uri = "hp:/usb/PSC_750?serial=MY2AED40PTWB"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
date_time = 07/10/2010 18:51:41
version = 3.10.2rc1.9

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
  --------------------------------  ----------------
  hp:/usb/PSC_750?serial=MY2AED40P  HP PSC 750      
  TWB                                               

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Hewlett-Packard-PSC-750
-----------------------
Type: Unknown
Device URI: usb://HP/PSC%20750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/Hewlett-Packard-PSC-750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer Hewlett-Packard-PSC-750 is idle.  enabled since Sat 10 Jul 2010 Invalid printer command "Clean"!
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_750
-------
Type: Printer
Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/PSC_750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer PSC_750 is idle.  enabled since Sat 10 Jul 2010 06:47:33 PM MST
error: Device busy: hp:/usb/PSC_750?serial=MY2AED40PTWB
error: Device not found
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_750?serial=MY2AED40PTWB' is a Hewlett-Packard PSC_750 all-in-one


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

HP Device 0x1411 at 002:002: 
    Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
    Device node: /dev/bus/usb/002/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

thomas adm dialout cdrom plugdev lpadmin admin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 7 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes libcupsimage2-dev
sudo aptitude install --assume-yes build-essential
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libtool
sudo aptitude install --assume-yes python-dev

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
thomas@thomas-desktop:~$ 

Does the assume-yes mean that the stuff was installed?

---

### Post by Georgia boy on 2010-07-10
redid the hp-check and got the following now:

thomas@thomas-desktop:~$ sudo hp-check -r

HP Linux Imaging and Printing System (ver. 3.10.2)
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
Linux thomas-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

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
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

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


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
working_dir = .
device_uri = "hp:/usb/PSC_750?serial=MY2AED40PTWB"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
date_time = 07/10/2010 18:51:41
version = 3.10.2rc1.9

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
  --------------------------------  ----------------
  hp:/usb/PSC_750?serial=MY2AED40P  HP PSC 750      
  TWB                                               

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Hewlett-Packard-PSC-750
-----------------------
Type: Unknown
Device URI: usb://HP/PSC%20750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/Hewlett-Packard-PSC-750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer Hewlett-Packard-PSC-750 is idle.  enabled since Sat 10 Jul 2010 Invalid printer command "Clean"!
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_750
-------
Type: Printer
Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/PSC_750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer PSC_750 is idle.  enabled since Sat 10 Jul 2010 06:47:33 PM MST
error: Device busy: hp:/usb/PSC_750?serial=MY2AED40PTWB
error: Device not found
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_750?serial=MY2AED40PTWB' is a Hewlett-Packard PSC_750 all-in-one


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

HP Device 0x1411 at 002:002: 
    Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
    Device node: /dev/bus/usb/002/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

root

error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.

-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
thomas@thomas-desktop:~$ 
 What do I need to get this fixed?
Still checking the rest of the information you sent.

Thanks

Tom

---

### Post by lidex on 2010-07-10
What's up with this?
> error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.


And this?
> warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP

Did you look at this section of help page?
'Setting up printers to use hplip'

---

### Post by Georgia boy on 2010-07-10
I had the HP tool box install the printer. System don't acknowledge that it's there. All of the things I read in the links you sent going into terminal I tried those. Xsane and Simple still don't acknowledge it. Have no idea of what it's talking about on the being a member of the LP groups. That popped up when doing the terminal on the HP-check thing. 
Still going through the links you sent trying to see if something comes about. Says that I have the latest HPLIP isntalled. Just nothing will recognize each other with it being installed properly.

The following is what you saw from where the printer was properly installed using the HP tool.

Hewlett-Packard-PSC-750
-----------------------
Type: Unknown
Device URI: usb://HP/PSC%20750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/Hewlett-Packard-PSC-750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer Hewlett-Packard-PSC-750 is idle. enabled since Sat 10 Jul 2010 Invalid printer command "Clean"!
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_750
-------
Type: Printer
Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/PSC_750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer PSC_750 is idle. enabled since Sat 10 Jul 2010 06:47:33 PM MST
error: Device busy: hp:/usb/PSC_750?serial=MY2AED40PTWB
error: Device not found
error: Communication status: Failed

Tom

---

### Post by Georgia boy on 2010-07-10
Here is a screen shot of the printer installed using the HP tools. As you can see it shows here, but all jobs hang and the printer seems to be invisible even though it was a system install. About to give up on this. Might have to get a new one someday. But until the printer completely stops I guess I'll just have to print with the way it prints from the other setup in my printer selections. Just will have to do without scanner looks like.
Tried the other links, followed other threads, nothing seems to be working for now. 

Thanks for the hard effort you went through trying to help. Really appreciate it very much!!!!

Thanks

Tom

---

### Post by lidex on 2010-07-10
Go to 'System>Administration>Users and Groups'. Click 'Manage Groups' select 'lp' and click 'Properties' check to select yourself as a member. Click 'OK'. Now repeat that process with 'lpadmin' and 'saned'

---

### Post by Georgia boy on 2010-07-11
Did as you mentioned. Redid the hp-check: as you can see it still don't see the one printer.
Here's what followed:

thomas@thomas-desktop:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.10.2)
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
Linux thomas-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
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

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsimage2-dev

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes build-essential

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

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
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

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


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
working_dir = .
device_uri = "hp:/usb/PSC_750?serial=MY2AED40PTWB"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.2rc1.9
date_time = 07/10/2010 21:10:00

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
  --------------------------------  ----------------
  hp:/usb/PSC_750?serial=MY2AED40P  HP PSC 750      
  TWB                                               

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Hewlett-Packard-PSC-750
-----------------------
Type: Unknown
Device URI: usb://HP/PSC%20750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/Hewlett-Packard-PSC-750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer Hewlett-Packard-PSC-750 is idle.  enabled since Sat 10 Jul 2010 Invalid printer command "Clean"!
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_750
-------
Type: Printer
Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/PSC_750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer PSC_750 is idle.  enabled since Sat 10 Jul 2010 09:03:46 PM MST
error: Device busy: hp:/usb/PSC_750?serial=MY2AED40PTWB
error: Device not found
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_750?serial=MY2AED40PTWB' is a Hewlett-Packard PSC_750 all-in-one


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

HP Device 0x1411 at 002:002: 
    Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
    Device node: /dev/bus/usb/002/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

thomas adm dialout cdrom plugdev lpadmin admin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 7 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes libcupsimage2-dev
sudo aptitude install --assume-yes build-essential
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libtool
sudo aptitude install --assume-yes python-dev

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
thomas@thomas-desktop:~$

---

### Post by Georgia boy on 2010-07-11
Sudo scan image-l:

thomas@thomas-desktop:~$ sudo scanimage -L 
device `hpaio:/usb/PSC_750?serial=MY2AED40PTWB' is a Hewlett-Packard PSC_750 all-in-one
thomas@thomas-desktop:~$

---

### Post by Georgia boy on 2010-07-11
Did all adds by clicking the check box by my name in the properties of all three items to no avail. Didn't do the add, just the properties as you mentioned. But still no go. Ouch. It just don't want to recognize the printer setup. 

Tom

---

### Post by lidex on 2010-07-11
Did you run these commands:
```
sudo aptitude install --assume-yes libcupsimage2-dev
sudo aptitude install --assume-yes build-essential
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libtool
sudo aptitude install --assume-yes python-dev

```

It also shows you are not a member of lp group.

---

### Post by Georgia boy on 2010-07-11
Hi Lidex! Was busy this morning. Plus wife took me out to lunch. Just got back on. Ran the commands. Here is a new run of hp-check. Don't know why it keeps saying about installation with HLIP. I ran the HP tool box and installed printer that way. 
???

Thanks

Tom

---

### Post by Georgia boy on 2010-07-11
Oooops. Forgot the copy of what I found in terminal. Mind not there after a nice lunch.

thomas@thomas-desktop:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.10.2)
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
Linux thomas-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
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
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

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


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
working_dir = .
device_uri = "hp:/usb/PSC_750?serial=MY2AED40PTWB"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.2rc1.9
date_time = 07/11/2010 15:29:32

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
  --------------------------------  ----------------
  hp:/usb/PSC_750?serial=MY2AED40P  HP PSC 750      
  TWB                                               

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Hewlett-Packard-PSC-750
-----------------------
Type: Unknown
Device URI: usb://HP/PSC%20750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/Hewlett-Packard-PSC-750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer Hewlett-Packard-PSC-750 is idle.  enabled since Sat 10 Jul 2010 09:01:05 PM MST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_750
-------
Type: Printer
Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/PSC_750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer PSC_750 is idle.  enabled since Sat 10 Jul 2010 09:03:46 PM MST
error: Device busy: hp:/usb/PSC_750?serial=MY2AED40PTWB
error: Device not found
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_750?serial=MY2AED40PTWB' is a Hewlett-Packard PSC_750 all-in-one


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

HP Device 0x1411 at 002:002: 
    Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
    Device node: /dev/bus/usb/002/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

thomas adm lp dialout cdrom plugdev lpadmin saned admin sambashare

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
thomas@thomas-desktop:~$

---

### Post by lidex on 2010-07-11
Troubleshooting
Run:
```
sudo hp-check -r
```
This will summarize any installation errors. 
```
Setting up printers to use hplip.

Known to work with: hppsc 1210. i don't have another printer, but this works well for me.

Preamble: So you want your printer to scan and print? but you also want the tools from HP to go with it! This is fairly simple, just takes a bit of configuration.

Step 1: run synaptic (system > admin > synaptic). Put in your password, and search for 'hplip'.

Install all three packages, then move to step two.

Step 2: once the tools are installed, you will need to restart your printer, and also run /etc/init.d/cupsys restart, to update your cups interface. this is CRUCIAL!

Step 3: Go and download the appropriate module for your printer (gimp-print doesn't have the correct modules for PSC model printers, so goto http://www.openprinting.org/printers and get the driver for your printer (about 20kb)). Copy this driver into the folder of your choice (i chose /usr/share/hplip/data, remember the folder because you're going to need it in the next step).

Step 4: run system -> administration -> printers, input your password, and install a new printer. Do NOT use the detected printers, use the location that appears when you select "Use another printer by specifying a port". Click next, goto HP at the top (if it isn't already selected), then goto Install Driver. Select the ppd file from your location, so in my case /usr/share/hplip/data/hp_psc_1210.ppd, and then follow the prompts until it finishes.

Step 5: add hpaio to the end of /etc/sane.d/dll.conf. This is so the sane backend can work with hplip.

Step 6: test page baybee! if it works, run xsane and give the scanner a run and you're good to go!

Known problems: I haven't found anything. The hp-toolbox (system -> preferances -> hp toolbox) seems acurate, and... well, everything just works. what else could you want? -

Above does not work for networked printers. I got my hp laserjet 1200 to be seen by hplip as follows:

Grab the ppd file as detailed above.

Run hp-makeuri IPADDRESS where IPADDRESS is your printers local ip address (mine is 192.168.0.150). Save the result

Mine was: hp:/net/HP_LaserJet_1200?ip=192.168.0.150

Install kprinter. The gnome printool does not allow installation of hp:// addresses at present (correct me if I'm wrong please)

sudo kprinter

click on install wand and follow wizard

Click on "other printer type"

Insert uri produced by hp-makeuri command

Click "other" at driver step and select the ppd file.

Click to finish and REBOOT machine (a cupsys restart was not enough for me).

On restart hplip should pick up networked printer as well as your local ones. 
```

---

### Post by Georgia boy on 2010-07-11
Why does it now say I need to be a member of lp and lpadmin when I did what you mentioned last night of going into the user groups and manage groups and then the properties of those three and clicking of the check box by my name? I just checked and they were all still checked.

thomas@thomas-desktop:~$ sudo hp-check -r

HP Linux Imaging and Printing System (ver. 3.10.2)
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
Linux thomas-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

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
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

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


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
working_dir = .
device_uri = "hp:/usb/PSC_750?serial=MY2AED40PTWB"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.2rc1.9
date_time = 07/11/2010 15:29:32

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
  --------------------------------  ----------------
  hp:/usb/PSC_750?serial=MY2AED40P  HP PSC 750      
  TWB                                               

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Hewlett-Packard-PSC-750
-----------------------
Type: Unknown
Device URI: usb://HP/PSC%20750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/Hewlett-Packard-PSC-750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer Hewlett-Packard-PSC-750 is idle.  enabled since Sat 10 Jul 2010 09:01:05 PM MST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_750
-------
Type: Printer
Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
PPD: /etc/cups/ppd/PSC_750.ppd
PPD Description: HP PSC 750 hpijs, 3.10.2
Printer status: printer PSC_750 is idle.  enabled since Sat 10 Jul 2010 09:03:46 PM MST
error: Device busy: hp:/usb/PSC_750?serial=MY2AED40PTWB
error: Device not found
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_750?serial=MY2AED40PTWB' is a Hewlett-Packard PSC_750 all-in-one


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

HP Device 0x1411 at 002:002: 
    Device URI: hp:/usb/PSC_750?serial=MY2AED40PTWB
    Device node: /dev/bus/usb/002/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

root

error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.

-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
thomas@thomas-desktop:~$

---

### Post by Georgia boy on 2010-07-11
Here is a screen shot of what I have installed of HPLIP. As you can see there are two items not installed. Don't know if they should be or not.
Take a look and see what you think.

Thanks

Tom

---

### Post by Georgia boy on 2010-07-11
Noticed this on the Open printer site:

You have selected Ubuntu 10.04 using the HP PSC 750 All-in-one Printer.

Ubuntu 10.04 supplies HPLIP 3.10.2 and it does support your printer.

As the version of HPLIP supplied with your operating system supports your printer, you may continue to use that version of HPLIP.

So, I've got a version that Lucid supplied and it supposedly supports my printer. How do I get it to do so? 

Thanks
Tom

---

### Post by lidex on 2010-07-11
The last time you ran it with sudo. If you look closely you'll see that 'Root' is not a member of those groups. The previous time you did it without sudo and it showed correctly you are in those groups. In any case all you have to do is fix the errors/warnings and it should work. Mainly this:
```
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
```

Make sure these are installed then follow the instructions in my last post beginning with step 2:
```
hplip
hplip-cups
hplip-data
```

---

### Post by Georgia boy on 2010-07-11
Tried doing this but unable to get command to go through. 
add hpaio to the end of /etc/sane.d/dll.conf.

Tom

---

### Post by lidex on 2010-07-11
Try editing it like this:
```
gksudo gedit /etc/sane.d/dll.conf
```
Save and close.

---

### Post by Georgia boy on 2010-07-11
Look at my other thread. I'm stuck in the terminal now after doing the update of hplip driver. Had to change into the desktop to do the update but now can't get back to regular terminal. Any way of correcting this except for reinstalling Lucid?

Tom

---

### Post by Georgia boy on 2010-07-11
Downloaded the new version of HPLIP, went to synaptic and got the HPLIP things all checked and downloaded. However, the printer installed with the new stuff just wont even print. Don't want to be recognized at all even when sending test prints to it. Pain in the buns.

Tom

---

### Post by Georgia boy on 2010-07-14
Sorry for taking so long. Was busy. Did this: gksudo gedit /etc/sane.d/dll.conf. Noticed that hpaio was listed at the very bottom. So, don't know what's next. See so many problems lately here with printer/scanner going on. 

Tom

---

### Post by michalmisiu on 2010-07-15
Same printer, same problem ... solved :
1. For a while, enable "lucid-proposed" ([https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)),
2. Update "libusb-0.1-4" to "2:0.1.12-14ubuntu02" version (from lucid-proposed repo)
3. Maybe (!) must reconfigure PSC-750 printer (simple delete PSC under "administration" printers and add a default configuration of a PSC (or wait a while)).

---

### Post by Georgia boy on 2010-07-16
michalmisiu! You're my hero!!!
Thank you very much. I did the proposed like you suggested. Went and did the search on the lsub versioin. Saw that it was installed, however I wend and did a reinstall. Did the apply. Deleted the PSC that the system had installed and left the one I had with the USB connection. Rebooted my machine. Turned on the printer and did a simple scan. Worked!!!!!

I was about to start pulling my greying hair out on this one.](*,) Don't know why it started happening but it started with the printer not being seen then the scanner started acting up like that. 

Keeping my fingers crossed on this staying. But tried it out and so far it sticks. 

I have a question that all can jump in on with their views. Should the proposed be always checked or not? What exactly is it for? Curious.

Thanks everyone for being involved and helping with this thread. I was getting upset with this thing and was thinking of getting another PSC at a later date with this acting up the way it was. But, now thanks to all I can put that off to a real later date!!!!!   :-)

Have a great day and a wonderful weekend everyone!!!

Thanks

Tom

---

### Post by philinux on 2010-07-16
> **Georgia boy said:**
> 

I have a question that all can jump in on with their views. Should the proposed be always checked or not? What exactly is it for? Curious.


Thanks

Tom

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Georgia boy on 2010-07-16
Thanks for the info Phil. If I'm reading this right then I shouldn't have it ticked all the time unless I want to be involved in testing. Since I'm not that good with stuff yet I probably should leave all the way I have it and only go there when suggested to fix something like what happened to my scanner.

Have a wonderful weekend!!

Tom

---

### Post by Georgia boy on 2010-07-17
Going to mark this as solved due to now working. Keeping fingers crossed that it continues to work and that I don't have to replace with another one for a long time to come.
I wish to thank everyone for their help in solving this problem. I was pulling my hair trying to figure why all of a sudden it quit and that nothing I did would work. 
Seems to be a lot of printer/scanner problems with this version for some reason. 

Well again, thanks everyone and I hope that all have a wonderful weekend.

Tom

---

