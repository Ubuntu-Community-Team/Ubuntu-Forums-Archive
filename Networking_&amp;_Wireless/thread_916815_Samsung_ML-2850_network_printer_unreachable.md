---
title: "Samsung ML-2850 network printer unreachable"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by glacialfury on 2008-09-11
Hi.  I recently bought a Samsung ML-2850 network/duplex laser printer.  According to [http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-2851ND](http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-2851ND) , it should work perfectly.

1) I hooked it up to my router via the instructions that came with the printer.

2) I inserted the CD from Samsung (which contains Linux drivers), and it asked to autorun a program.  I said yes, nothing happened.

3) Assuming it was because the CD was not running with root privileges, I opened a terminal and ran the installation script on the CD with sudo.  The installation GUI popped up and all went according to plan.  The printer driver was installed and configurable.  

4) I attempted to print the test page.  The test page failed to print, and eventually a systray message popped up saying "Not connected?  Printer 'ML2850' may not be connected."

5) I examined the router page of attached devices and confirmed that, indeed, the printer was listed as being connected.  I checked the cables which were all firmly plugged in.  The printer was on, and could successfully print the demo page when the printer button was pushed.  I printed the configuration page, which listed the printer's IP as 192.0.0.192, as well as the MAC address.

6) On the router's attached devices page, there were no devices with that MAC address, although the connectivity light is on by the port where the printer is plugged in to the router.  I know the DHCP range for the router is 192.168.1.x - 192.168.1.y; could it be that they simply can't see each other?  I thought the router was supposed to see and assign things connected to it automatically.

I would very much like to get this printer working, and it supposedly has good Linux support.  Any ideas?  Any help?

---

### Post by Loïc2 on 2008-11-16
Don't use the Linux drivers from the CD, Ubuntu already has what you need.

Since you used them, and I don't know what they install, if the following doesn't work you might just have to reinstall.

- open Administration>Printer, then either new printer or new network printer.

- choose Samsung, then the model of your printer: 2850 (mine is 2851, they should be the same).

Basically, you're done. If you want to access all the options, when you're asked if you want to put a custom PPD file, give the one that comes with the CD.

To get this PPD file, install one of the Windows drivers with wine, then you'll just have to get the file that end with .ppd or .PPD.

To find it if you really can't, cd into the wine directory:
cd .wine
then :
find | grep PPD
find | grep ppd

---

