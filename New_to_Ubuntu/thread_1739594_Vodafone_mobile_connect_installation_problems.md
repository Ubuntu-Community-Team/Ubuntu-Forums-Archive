---
title: "Vodafone mobile connect installation problems"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by fabby2611 on 2011-04-26
I am new to Ubuntu. I have failed to connect by vodafone mobile broadband usb stick(modem),
I am using Ubuntu 10.10 intalled via wubi:

**I have this instructions from the web:**

VODAFONE MOBILE CONNECT INSTALLATION INSTRUCTIONS.

-------------------------------------------------


* You need a previously working internet connection (e.g: your ethernet one)

* Download from this page these two DEB packages:

     - usb-modeswitch
     - vodafone-mobile-connect

* Install them, e.g: in a terminal command line (substitute the version and architecture here for the ones you have downloaded)

     sudo dpkg -i usb-modeswitch_0.9.4-1_i386.deb
     sudo dpkg -i vodafone-mobile-connect_1.99.17-8_all.deb

* After this step, you will possibly have unresolved dependencies problems. To solve them execute:

     sudo apt-get -f install  

* If everything has gone fine you can plug in the modem, and execute the driver with:

     vodafone-mobile-connect-card-driver-for-linux


[B]And when I apply them this is what the terminal looks like:
[/B]
faith@ubuntu:~$ sudo dpkg -i usb-modeswitch_0.9.7_i386.deb
[sudo] password for faith: 
Selecting previously deselected package usb-modeswitch.
(Reading database ... 118283 files and directories currently installed.)
Unpacking usb-modeswitch (from usb-modeswitch_0.9.7_i386.deb) ...
dpkg: dependency problems prevent configuration of usb-modeswitch:
 usb-modeswitch-data (20100826-1) breaks usb-modeswitch (<< 1.0.7-1) and is installed.
  Version of usb-modeswitch to be configured is 0.9.7.
dpkg: error processing usb-modeswitch (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 usb-modeswitch
faith@ubuntu:~$ sudo dpkg -i vodafone-mobile-connect_2.25.01-1_all.deb
Selecting previously deselected package vodafone-mobile-connect.
(Reading database ... 118285 files and directories currently installed.)
Unpacking vodafone-mobile-connect (from vodafone-mobile-connect_2.25.01-1_all.deb) ...
dpkg: dependency problems prevent configuration of vodafone-mobile-connect:
 vodafone-mobile-connect depends on hal; however:
  Package hal is not installed.
 vodafone-mobile-connect depends on ozerocdoff; however:
  Package ozerocdoff is not installed.
 vodafone-mobile-connect depends on python-twisted; however:
  Package python-twisted is not installed.
 vodafone-mobile-connect depends on python-tz; however:
  Package python-tz is not installed.
 vodafone-mobile-connect depends on usb-modeswitch (>= 0.9.7); however:
  Package usb-modeswitch is not configured yet.
 vodafone-mobile-connect depends on wvdial; however:
  Package wvdial is not installed.
dpkg: error processing vodafone-mobile-connect (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 vodafone-mobile-connect
faith@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED
  usb-modeswitch vodafone-mobile-connect
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 6,746kB disk space will be freed.
Do you want to continue [Y/n]? 

Many thanks for your help.
Please bear with me I am new.

---

### Post by 3rdalbum on 2011-04-26
You shouldn't actually need the Vodafone software. Are you saying that you can't set up your modem in the Network Manager applet?

The Network Manager applet is in the top panel, near the right side of the screen. If you left-click it, you can choose Edit Connections... and then go to the Mobile Broadband tab and click Add. Follow the prompts and that should be it.

---

### Post by Omar.Fayyad on 2011-08-31
> **3rdalbum said:**
> You shouldn't actually need the Vodafone software. Are you saying that you can't set up your modem in the Network Manager applet?

The Network Manager applet is in the top panel, near the right side of the screen. If you left-click it, you can choose Edit Connections... and then go to the Mobile Broadband tab and click Add. Follow the prompts and that should be it.


Hi,

Actuall i added a new broadband connection while i was with the tech team of vodafone and i after that it didn't signal !!! do you have any idea why ?


Appreciate your help

---

### Post by gandaran on 2011-09-01
> **Omar.Fayyad said:**
> Hi,

Actuall i added a new broadband connection while i was with the tech team of vodafone and i after that it didn't signal !!! do you have any idea why ?


Appreciate your help
which Ubuntu release do you have running? 11.04?
if it doesn't work on 11.04 using network manager try with Sakis3g
[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

