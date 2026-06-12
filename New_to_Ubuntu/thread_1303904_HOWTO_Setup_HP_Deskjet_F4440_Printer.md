---
title: "HOWTO: Setup HP Deskjet F4440 Printer"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by lkraemer on 2009-10-28
Here is a tutorial on setting up an HP Deskjet F4440 Printer for use
with Ubuntu 8.04.3 LTS.

I had already plugged in the printer to a USB port and it was located
and hpijs was recommended for the driver.......but the printer would
not print.

NOTE: INTENET CONNECTION IS REQUIRED.......

Some good information is found at:
[http://ubuntuforums.org/showthread.php?t=1276676&highlight=HP+Deskjet+F4440](http://ubuntuforums.org/showthread.php?t=1276676&highlight=HP+Deskjet+F4440)
Posting #9

That leads to more information:
[http://hplipopensource.com/hplip-web/supported_devices/combined.html](http://hplipopensource.com/hplip-web/supported_devices/combined.html)
[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4400_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4400_series.html)
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)


The HPLIP Automatic Installer

The Automatic Installer is known to work on the following Linux Distributions:

    * SUSE Linux (10.3, 11.0, 11, 11.1)
    * Fedora (9, 9.0, 10, 10.0, 11.0, 11)
    * Ubuntu (8.04, 8.04.1, 8.04.2, 8.10, 9.04)
    * Debian (4.0, 4.0r0, 4.0r1, 5.0, 5.0.1, lenny, lenny/sid, stable, testing)

To use the Automatic Installer, follow these steps:

       1. Download the file to a convenient location (e.g., home directory or desktop, etc).
           I used: /Downloads/HPLIP_398
       2. Open a console/terminal and cd to the location where the installer was downloaded.
           I used: cd /Downloads/HPLIP_398 
       3. Type in and run this command: 'sh hplip-3.9.8.run'


```

rick@rick-desktop:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          2.8.2-0ubuntu8 HP Linux Printing and Imaging System (HPLIP)
rick@rick-desktop:~$ cd Downloads
rick@rick-desktop:~/Downloads$ cd HPLIP_398
rick@rick-desktop:~/Downloads/HPLIP_398$ ls -alt
total 15388
drwxr-xr-x  2 rick rick     4096 2009-10-28 15:19 .
drwxr-xr-x 10 rick rick     4096 2009-10-28 15:19 ..
-rw-r--r--  1 rick rick 15724572 2009-10-28 15:18 hplip-3.9.8.run
rick@rick-desktop:~/Downloads/HPLIP_398$ sh hplip-3.9.8.run
Creating directory hplip-3.9.8
Verifying archive integrity... All good.
Uncompressing HPLIP 3.9.8 Self Extracting Archive..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.9.8)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Wed-28-Oct-2009_15:21:09.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...
 

INTRODUCTION
------------
This installer will install HPLIP version 3.9.8 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 8.04.

Is "Ubuntu 8.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 8 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: libpthread (libpthread - POSIX threads library)
warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 7 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4-dbus (PyQt 4 DBus - DBus Support for PyQt4)
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'fax': dbus (DBus - Message bus system)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo aptitude update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes python2.5-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libcupsys2-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes cupsys-bsd'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libusb-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libtool'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libjpeg62-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes openssl'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes python-qt4-dbus'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes python-reportlab'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libdbus-1-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libsane-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes sane-utils'
Please wait, this may take several minutes...
warning: A previous install of HPLIP is installed and/or running.
sudo apt-get remove --assume-yes hplip hpijs foomatic-db-hpijs (Removing old HPLIP version)
warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
warning: Continuing to run installer - this installation should overwrite the previous one.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
 

PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-qt4 --enable-doc-build --enable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --enable-policykit --disable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
Command completed successfully.

Running 'sudo make install'
Please wait, this may take several minutes...
Command completed successfully.


Build complete.


POST-BUILD COMMANDS
-------------------
sudo sh /etc/init.d/dbus reload (Post-build step 1)


RESTART OR RE-PLUG IS REQUIRED
------------------------------
If you are installing a USB connected printer, and the printer was plugged in   
when you started this installer, you will need to either restart your PC or     
unplug and re-plug in your printer (USB cable only). If you choose to restart,  
run this command after restarting: hp-setup (Note: If you are using a parallel  
connection, you will have to restart your PC. If you are using network/wireless,
you can ignore and continue).                                                   

Restart or re-plug in your printer (r=restart, p=re-plug in*, i=ignore/continue, q=quit) : p
Please unplug and re-plugin your printer now.  Press <enter> to continue or 'q' to quit: 


PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
rick@rick-desktop:~/Downloads/HPLIP_398$

```

The printer now prints correctly.

lk

---

