---
title: "HP Deskjet 1050"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by bungz on 2011-03-13
Hi folks,

Got this new printer/scanner. How do i go about installing it and making both work? 

My comp seems to recognize the printer, but is not printing when i print test page or any other page. 

I have absolutely no clue with the scanner. 

Would appreciate any help. 

Thanks.

---

### Post by rosencrantz on 2011-03-13
What hplip version do you have? (check e.g. dpkg -l | grep hplip)
Your printer is not supported by older versions, so you might want to update, as described here: [http://winunixmac.com/tips-and-tricks/74-how-to-configure-a-hp-deskjet-1050-on-ubuntu](http://winunixmac.com/tips-and-tricks/74-how-to-configure-a-hp-deskjet-1050-on-ubuntu)
Not quite sure whether that will solve the scanning issue, try starting xsane after the hplip update and see what it comes up with.

Cheers,
rosencrantz

---

### Post by shredder12 on 2011-03-13
I had trouble running my HP printer too - Deskjet 1000 j110. I had the same issue, was able to recognize and configure but couldn't print a test page. I wrote the whole work around here.
[URL="http://linuxers.org/howto/how-setup-and-configure-hp-printer-or-scanner-ubuntu-or-fedora-linux"]http://linuxers.org/howto/how-setup-and-configure-hp-printer-or-scanner-ubuntu-or-fedora-linux
[/URL]
Hope it helps.

---

### Post by bungz on 2011-03-13
hplip on my comp is indeed the older version. 3.9.8 i think. 

Anyways, i tried installing the newer version and i keep getting an error message following instructions from here: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html). 

Posting below what's been happening:
[PHP]
bungi@the:~$ cd Desktop
bungi@the:~/Desktop$ sh hplip-3.11.1.run
Creating directory hplip-3.11.1
Verifying archive integrity... All good.
Uncompressing HPLIP 3.11.1 Self Extracting Archive...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.11.1)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Mon-14-Mar-2011_06:00:13.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...
|/home/bungi/.themes/Clearlooks-LemonGraphite/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/bungi/.themes/Clearlooks-LemonGraphite/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/bungi/.themes/Clearlooks-LemonGraphite/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/bungi/.themes/Clearlooks-LemonGraphite/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
 

INTRODUCTION
------------
This installer will install HPLIP version 3.11.1 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 9.10.

Is "Ubuntu 9.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the user (bungi)'s password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.  During the install process you will be added to the lp group, please quit the installer before the setup stage, log out, log back in, and run hp-setup to complete the install.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 5 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 8 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4-dbus (PyQt 4 DBus - DBus Support for PyQt4)
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4 (PyQt 4- Qt interface for Python (for Qt version 4.x))
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'fax': dbus (DBus - Message bus system)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'base': cups-ddk (CUPS DDK - CUPS driver development kit)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes libcupsys2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes libcupsys2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes libcupsys2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes libcupsys2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --assume-yes libcupsys2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? [/PHP]Any idea on what's happening? :confused:

---

### Post by bungz on 2011-03-13
@Shredder12 - How do i install the missing dependencies?

---

### Post by bungz on 2011-03-13
How do i install missing dependencies?

---

### Post by bungz on 2011-03-13
All right. Issue sorted. Thanks for all the help and pointing me in the right direction, folks. :)

I used the search option in the synaptic package manager to individually install the missing dependencies listed in the terminal. 

Installation went smoothly after that. 

Useful sites for this issue:
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
[http://linuxers.org/howto/how-setup-and-configure-hp-printer-or-scanner-ubuntu-or-fedora-linux](http://linuxers.org/howto/how-setup-and-configure-hp-printer-or-scanner-ubuntu-or-fedora-linux)

---

