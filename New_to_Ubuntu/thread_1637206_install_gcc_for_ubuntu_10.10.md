---
title: "install gcc for ubuntu 10.10"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by havtrouble on 2010-12-04
Hello all,
I am new to Ubuntu. I had recently installed a Ubuntu10.10 on my Toshiba Satellite L-310 laptop. I find that my HP Laserjet 1020 printer was not being recoganized by the OS. I visited the HP site and downloaded the recommended installer(?) "hplip-3.10.9" While attempting to run the installer I get the message
" INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.":
When I google gcc GNU Project C and C+++ Compiler, I am just not able to find the installer (if that's the word) from any of the pages. What do I do to install the "missing dependencies" ?
I will be grateful if I am pointed in the correct direction. I know nothing of Ubuntu. So I dont know if the title for this thread is apt. Any help is appreciated

---

### Post by wojox on 2010-12-04
Try:

```
sudo apt-get install gcc build-essential
```

---

### Post by XeonBloomfield on 2010-12-04
Type in terminal:
```
sudo apt-get update
sudo apt-get install gcc
```

It will instal GCC in your system.

---

### Post by TeoBigusGeekus on 2010-12-04
```
sudo apt-get install build-essential
```
from terminal.

---

### Post by XeonBloomfield on 2010-12-04
Arghh...

I forgot about build-essential. Better install it.

---

### Post by havtrouble on 2010-12-06
Thanks for all that responses.
I did all of that and tried to install "hplip-3.10.9.run" so that I can use my laserjet printer. Now I get the error

"warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: This installer cannot install 'python-devel' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer."

How do I manually install this ?
Thank you once again

---

### Post by TeoBigusGeekus on 2010-12-06
Try
```
sudo apt-get install python-devel
```

---

### Post by havtrouble on 2010-12-06
Thanks for the reply
Tried it.. The response is "E: Unable to locate package python-devel"

---

### Post by TeoBigusGeekus on 2010-12-06
Then open synaptic package manager and search for python.
When it finds something like python-devel install it and try again.

---

### Post by havtrouble on 2010-12-06
Thanks TeoBigusGeekus.
But I fail to understand the advice. 

 "Then open synaptic package manager and search for python. When it finds something like python-devel install it and try again"

What is "synaptic package manager". I am new and dumb.

---

### Post by kyle6513 on 2010-12-06
synaptic package manager is a big collection of all the programs that ubuntu has in it's respiratories. It is located under system>administration>synaptic package manager

in there you will need to use search to find any package you want, anything that this program you are trying to install tells you it needs, you use this program to find it until it works.

good luck!

---

### Post by TeoBigusGeekus on 2010-12-06
System>Administration>Synaptic Package Manager.
Put python in the search field (top rightish) and press enter.
Skim through the results. Do you find something like python-devel?

---

### Post by arjunlalb on 2010-12-06
sudo apt-get install build-essential
sudo apt-get install update
sudo apt-get install gcc

---

### Post by NightwishFan on 2010-12-06
This will sort you out, this is the package you want (auto install)
[Install Python Dev]("apt://python-dev")

If that doesnt work, run:
```
sudo apt-get install python-dev
```

---

### Post by ac7nj on 2010-12-06
use synaptic package manager it will automaticly get the dependancies you need.

---

### Post by havtrouble on 2010-12-07
Thanks to all of you, I found the Synaptic Package Manager and search for "python" yielded a lot of pythons:)  But the one I searched for is python-devel but the closest result is python-tg.devtools. Dont know If it is the same thing that I am looking for. So tried the auto-install and the page just stalled for 30 minutes showing the message "installing" and nothing was happening. (see screenshot)
So I tried  sudo apt-get install pyhton-dev and was successful

Then I tried to install hplip-3.10.9.run and now the error message is 

"warning: There are 5 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: This installer cannot install 'cups-devel' for your distro/OS and/or version."

Searched  for CUPS devel in the Synaptic Package Manager and the closest result is "cups" (and not CUPS devel ) Are these two the same?  The cups in my Synaptic Package Manager is installed. See screenshot
I think I see some pattern here. Should I run
>  sudo apt-get install CUPS-dev


---

### Post by Starring on 2010-12-07
[FONT=Verdana]Hi, i'm also new on Ubuntu and Linux in general.

I googled the same problem and found this thread.
Now, with the help of this forum i moved on and got the installatin of HPLIP-3.10.9 completed.
This is the way i managed it:

I looked on this page: [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)
There was only the way of Ubuntu 10.04, but i tried to copy&paste it. Got an error [/FONT][FONT=monospace][FONT=Verdana]on aptitude.

Here the parameters:
[/FONT][/FONT]sudo aptitude install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane

[FONT=monospace][FONT=Verdana]

So i looked on the parameters given and compared them with the required dependencies. Now i used the Synaptic Package Manager to get the compared packages, where i found the required ones, installed them step by step and got finally no more missing dependencies.

Hope this will help. Sorry for my bad english, trying to improve my skills.
[/FONT][/FONT]

---

### Post by havtrouble on 2010-12-07
Thanks for the help
I visited the page [http://hplipopensource.com/hplip-web...os/ubuntu.html](http://hplipopensource.com/hplip-web...os/ubuntu.html) and tried to run the command
> sudo aptitude install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client
 libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl 
libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 
policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject 
python-dev python-notify python python-reportlab libsane libsane-dev 
sane-utils xsane


I ran this after copy-paste from the above page and the result I get is 
> sudo: aptitude: command not found

---

### Post by havtrouble on 2010-12-07
Thank you Starring. You showed me how to get all the "missing dependencies" I still havent understood what exactly those steps meant but having done them mechanically I have my hp printer recoganized and done what I need to do on the printer. This particular problem is solved. Let me head out and create new threads for new problems

---

### Post by machshadow on 2010-12-07
For those who are running 10.10; the long command line above, instead of sudo aptitude, it is going to be sudo apt-get install ......



> sudo apt-get install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client
libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl 
libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 
policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject 
python-dev python-notify python python-reportlab libsane libsane-dev 
sane-utils xsane

---

### Post by anewguy on 2010-12-07
One thing for people to keep in mind - gcc (and I believe g++ but could be wrong on that one) are supposed to be included when you install the build-essential package, so there is no need to add another get for gcc.

To the OP:

In case nobody has made somethings clearer for you:

each piece of software has things it "depends" on to run - GTK for a lot of GUI's applications, varying run time libraries, etc..  When you use the preferred method of adding software packages, Synaptic Package Manager, it will be sure the packages that the software "depends" on - the "dependencies", are installed as well.  Sometimes a piece of software is not in the package manager - I suspect this is probably the case with what you are trying to install.  In such cases, unless the package includes the dependencies, you have to install them yourself.  When getting a software package from somewhere other than the package manager (or Ubuntu Software Center), it's best to check the website and any readme files for dependencies and install those before proceeding.

What you are running up against is this lack of the packages the software depends on.

If you grabbed the software via Synaptic Package Manager, it should have installed them.  If you used apt-get, you may want to try sudo apt-get build-dep <package name>.  This will build the dependencies list for you.

Dave ;)

---

### Post by havtrouble on 2010-12-08
Thanks for that post, anewguy. I had to read that post 3-4 times and it confirms what I had guessed regarding software dependencies. Thanks a lot.

---

### Post by anewguy on 2010-12-08
Doesn't solve your problem, but thought it might help clarify why some things are happening.

Dave ;)

---

### Post by mikebravo on 2011-01-16
Are we noobs doing something fundamentally wrong with Ubuntu? Doing something as basic as installing a name brand printer has not been so much a PITA since Windows 3.1.   Some of us download Ubuntu and burn the iso, others buy it pre cut on a cd from a distributor. Would we get all the files we needed if we bought the DVD set? Could Ubuntu find them if it needed them? This chasing around for dependencies is not cool.

---

### Post by JKyleOKC on 2011-01-16
> **mikebravo said:**
> Are we noobs doing something fundamentally wrong with Ubuntu? Doing something as basic as installing a name brand printer has not been so much a PITA since Windows 3.1.Unfortunately, yes, you did make a quite common mistake: you got the driver file from the HP site instead of asking first here.

Unlike Windows, the Ubuntu distribution maintains a quite large "repository" of packages, including printer drivers. All of them have been set up and tested to make sure that they work, normally "out of the box," with the Ubuntu systems. I just searched for "hplip" in the repository, and came up with an even dozen packages.

It's always best to search the repositories first. Depending on which version of Ubuntu you are running, this may be done through the Ubuntu Software Center (a program), or through Synaptic, which is another program that looks in the same places but provides more technical details about the programs.

Both programs include search features that help greatly in locating specific programs even if you don't know the exact names. Only if your search fails do you need to ask for help here in the forums. Doing a full Google search and downloading things from other sites should be considered as only a last resort -- if for no better reason than that packages you install by this means won't ever get automatic security updates when needed!

---

### Post by mikebravo on 2011-01-18
The response to this thread has been most helpful. Would someone please look at this and tell me how to pull my fat out of the fire:
      -------------------------------------------------------------
mike@ubuntu:~$ hp-check -b

HP Linux Imaging and Printing System (ver. 3.10.6)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to         
determine if the proper dependencies are installed to successfully compile HPLIP.                                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built  
HPLIP supplied tarball has the proper dependencies installed to successfully run.                                                    
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and   
run-time dependencies).                                                                                                              

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux ubuntu 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.10

Checking Python version...
OK, version 2.6.6 installed

Checking PyQt 4.x version...
OK, version 4.7.4 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.4
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
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

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
HPLIP 3.10.6 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.6

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
internal-tag=3.10.6.15
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
working_dir = /usr/bin/hpijs
device_uri = "hpfax:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ2248KPR1a"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.6.15
date_time = 01/18/2011 17:44:58

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

  Device URI                                            Model                               
  ----------------------------------------------------  ------------------------------------
  hp:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=  HP LaserJet Professional M1212nf MFP
  000000000QJ2248KPR1a                                                                      

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP-LaserJet-Professional-M1212nf-MFP
------------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ2248KPR1a
PPD: /etc/cups/ppd/HP-LaserJet-Professional-M1212nf-MFP.ppd
PPD Description: HP LaserJet Professional m1212nf MFP hpijs, 3.10.6
Printer status: printer HP-LaserJet-Professional-M1212nf-MFP is idle.  enabled since Tue 18 Jan 2011 04:13:39 PM CST
error: Required plug-in status: Not installed
Communication status: Good

HP-LaserJet-Professional-M1212nf-MFP-Fax-3
------------------------------------------
Type: Fax
Device URI: hpfax:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ2248KPR1a
PPD: /etc/cups/ppd/HP-LaserJet-Professional-M1212nf-MFP-Fax-3.ppd
PPD Description: HP Fax3 hpijs
Printer status: printer HP-LaserJet-Professional-M1212nf-MFP-Fax-3 is idle.  enabled since Tue 18 Jan 2011 04:13:44 PM CST
error: Required plug-in status: Not installed
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ2248KPR1a' is a Hewlett-Packard HP_LaserJet_Professional_M1212nf_MFP all-in-one


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

HP Device 0x52a at 001:002: 
    Device URI: hp:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ2248KPR1a
    Device node: /dev/bus/usb/001/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

mike adm dialout cdrom audio video plugdev lpadmin admin nopasswdlogin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
mike@ubuntu:~$ 
   -------------------------------------------------------------------

I looked in the synaptic package manager and found nothing that looks like "libnetsnmp-devel". Does it go by another name in Ubuntu?

What are the names of the "required plugins", where do I find them, and how do I install them?

One more thing I have no clue about is the dialog box that pops up and says "HPLIP Status Service: No system tray detected on this system. Unable to start, exiting."

I do not care if the scanner does not work but I would really like to print.

---

### Post by mikebravo on 2011-01-18
Deleted duplicate post.

---

### Post by JKyleOKC on 2011-01-18
For the dependency problem, have a look at [http://ubuntuforums.org/showthread.php?t=1381045](http://ubuntuforums.org/showthread.php?t=1381045) which deals with this same problem. I found it via a Google search for "libnetsnmp-devel ubuntu" and that also referenced several other threads, which I've not yet read -- but they might help with your other issues.

My HP Laserjet 3020 installed perfectly out of the box using CUPS, with no need to deal with the HPLIP program (and its accompanying bloat, which was considerable when I was running it on Windows before moving my printer to a *buntu box). This wouldn't help with the fax or scanner capabilities, though...

---

### Post by kiers on 2011-01-19
> **JKyleOKC said:**
> Unfortunately, yes, you did make a quite common mistake: you got the driver file from the HP site instead of asking first here.

... Doing a full Google search and downloading things from other sites should be considered as only a last resort -- if for no better reason than that packages you install by this means won't ever get automatic security updates when needed!

AMEN X 100!!! 
Let me tell u, I was trying to install a HP AIO K209a!

I *blindly* :o (trustingly) ran the "hplip.run" package w/o relying on my already existent, repository-provided hplip & hpaio packages!

AND, as righteously mentioned by JKyleOKC,  this killer(!) shell script provided by HP engineers (I KNOW on their website, it says "HP not involved", also hplipopensource.com is a WHOLE different webpage, (warning!) OUTSIDE "HP" corporate etc etc. etc. deny deny deny; but as you read further, the behaviour of this blaotware SMELLS of HP Corporate; not to mention that hplipopensource.com website IS DOWN for the entire daytime, every day, in the APAC region of the world ) FORTUNATELY crapped out on me needing g++ python dependencies etc. before it could DO MUCH DAMAGE! BUT THE LITTLE IT DID was E-N-U-F!

SO then I go to my "home" folder. (Note the words "my" home folder.) And what u know....it's SHotgun scattershot full of crappy HP configuration files python, xml, c, c++ which only an HP/MicroShaft engineer could love! (Makes windoze registry look like kindergarten)! OMG is this shell script BRUTAL(!) they don't even have the courtesy of "playing" in their separate subfolder. 

WARNING NOTE: when u run hplip.run u sign over "the keys to the kingdom" to this piece of...er bloatware: It asks for your sudo password FROM THE SCRIPT ITSELF. GOODBYE TO YOUR HAPPY PRIVATE UBUNTU ISLAND. HP Corporate just built a parking lot on your beach!!!! Then it does it's "business".

That's NOT ALL! Hplip.run changes your iptables(!) in firewall to allow access to god knows what: here's a piece : 

"iptables -L | egrep -q '427|svrloc'
if [ $? -ne 0 ]; then
    iptables -I INPUT 4 -p udp --sport 427 -j ACCEPT
    iptables-save >$conffile
fi

iptables -L | egrep -q '5353|mdns'
if [ $? -ne 0 ]; then
    iptables -I INPUT 4 -p udp --sport 5353 -j ACCEPT
    iptables-save >$conffile
fi

exit 0 "


WTF! WHO/WHAT gives them the right to do THAT?

Remember that scene in Event Horizon: "liberate mei" vs "liberate tutame"
SAME THING APPLIES HERE. SAVE YOURSELF. 

I'm running Maverick meerkat. OUT OF THE BOX, it can handle you HP AIO. I gave up on HPLIP when it crapped out on dependencies, (I Hope too much damage was NOT done) and just hooked up my new HP printer and it W-O-R-K-S. So does the scanner (under a separate app: "SimpleScan 2.32.

SAVE YOURSELF.

Ubuntu works out of box w HP.

---

### Post by chinmay3 on 2011-01-19
-

---

