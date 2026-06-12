---
title: "Setserial, drivers at boot time and S30etc-setserial"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2006-12-31
Dapper isn't reading the PCI bus / com ports or isn't setting them correctly. I guess. I'm not fluent in programming. I've been after this problem for months without success.

I finally came across some posts which seem to be about the problem I'm having (pppd/wvdial/modem disfunctional), the 'net doesn't stay connected and the software locks-up the modem. It can't reach the 'net and can't hang up either. Hence, dapper must be re-booted. The modem is a hardware-controller based internal modem.

What follows is mostly posts about my modem and several files involving rcS.d. I need to know if modifying those files will screw up more than just /etc/rcS.d/S30etc-setserial, so that I can set things right if necessary.

The posts want me to add these two lines:

setserial /dev/ttyS4 port c800 spd_vhi skip_test auto_irq autoconfig
setserial /dev/ttyS4 uart 16550A

I don't know what position (line number) they should be pasted into. Or whether they replace lines already in the file. (I would comment ## those unnecessary line), I don't know what they are.

What follows in blue is my  /etc/rcS.d/S30etc-setserial file:

[COLOR="Blue"]#! /bin/sh
# /etc/rc.serial
#       Initializes the serial ports on your system
#
# chkconfig: 2345 50 75
# description: This initializes the settings of the serial port
#
# Distributed with setserial version 2.15
#
# XXXX note: as of 2.15, the autosave feature doesn't work if you are
# using the multiport feature; it doesn't save the multiport configuration
# (for now).  Autosave also doesn't work for the hayes devices.
#Will fix later...
#
#
# Note that this has been changed so that if /etc/serial.conf exists,
# this script does not configure the ports. It uses
# /var/lib/setserial/autoserial.conf # instead, which is handled by another
# init.d script. However, the script is still used for module loads and
# unloads, even if serial.conf exists.
#

SETSERIAL=/bin/setserial
modconf=/var/run/setserial.conf
autoconfig=/var/lib/setserial/autoserial.conf
etcconfig=/etc/serial.conf

# If the serial executable has been removed abort the configuration
[ -x ${SETSERIAL} ] || exit 0[/COLOR]

What follows below, in orange are the posts that led me to think this is a solution to my problem:

[COLOR="DarkOrange"]Okay, the modem in question is the 3Com/USRobotics 3CP5610 PCI FaxModem.  It is one of the few PCI modems that is controller based, having an on-board 16550AF chip.  It is a K56 flex V.90 modem, which works very well for me.  The greatest problem that people have with this modem is that it installs on COM5 in Win9* and there is no com5 (by default) in linux.

This is where most people have trouble, and the way to get it to work is this:

1.  You need to configure your kernel to support more than 4 serial ports.  In /usr/src/linux, do a make xconfig and in the character devices setup, turn on (mark 'y') the "Extended dumb serial driver options" and turn on the "Support for more than 4 serial ports".  Then do a make bzImage and install the kernel (or whatever you do for the normal kernel make - if you have specific questions see the Kernel HOW-TO).
 
2.  Create the device file in /dev - namely /dev/ttyS4:  do this by

mknod -m 0640 /dev/ttyS4 c 4 68
ln -s /dev/ttyS4 /dev/modem

3.  In your /etc/rc.d/rc.local file, add the following line:

exec setserial /dev/ttyS4 irq ?? port 0x??? ^fourport
        ^auto_irq skip_test autoconfig spd_vhi

This sets up the device where you should replace the '?' with the correct values for your system.  These values can be found in the /proc/pci file, or you can get them from the windows system/hardware config info.

Reboot.  Point your kppp setup at /dev/modem, and everything should work.  It's important to include the ^fourport and skip_test in the setserial.  Otherwise, the kernel thinks that you have a serial expansion card installed, and the set-up will fail.

========================================================
from: [http://www.linux-sxs.org/](http://www.linux-sxs.org/)

PCI MODEMS - ACTIONTEC

This is a specific write up folks for a specific modem. If your modem IS pci, AND it is NOT a winmodem, these steps are most likely to work for you too!

WORKS FOR CALDERA OPEN LINUX 2.3 WHEN YOU HAVE AN ACTIONTEC INTERNAL 56k PCI CALL-WAITING MODEM.

ADDITIONAL INSTRUCTIONS FOR OTHER DISTRIBUTIONS OF LINUX are at end.
 

From: "Anthony Bridges" <sabr516@megsinet.net> (per the lllllama)

Here is what i found from the maker of my modem Actiontec. After a couple of e-mail to them and a visit to their site here is what makes this modem work in Linux. It is an easy to aquire modem. You can find it at most major electronics stores. It Work Great. And this modem is easy to go out and get if you are willing to spend a little money to get Open Linux online. Here is Actiontec's solution for their 56k Internal PCI Call-Waiting Modem...

Log on to Linux as root. Then from the KDE desktop click the terminal icon (the one that looks like two computers in the taskbar). Then type in the following command:

cat /proc/pci

The following is an example of information to look for when the computer return it to the screen:

Bus 0. device 12, function 0:
       Communication controller: Lucent (ex-AT&T)
       Microelectronics Unknown device (rev 0).
       Vendor id=11c1. Device id=480.
       Medium devsel. Fast back-to-back capable. IRQ 11. Master capable. No bursts. Min Gnt=252.Max Lat=14.
            Non-prefetchable 32 bit memory at 0xe0800000 [0xe0800000].
            I/O at 0xa000[0xa001].
            I/O at 0x9800 [0x9801].
            I/O at 0x9400 [0x9401].

Write down the first I/O range this example shows that I/O is 0xa000. The values may vary dependng on the system. Then Type:

setserial /dev/ttyS3 port 0xa000 spd_vhi skip_test auto_irq autoconfig

and hit enter. If there are no errors, then type:

setserial /dev/ttyS3 uart 16550A

and hit enter.

[Note : If you recieved errors during any of the preceding then you should check to make sure that the modem is in a PCI SLOT THAT CAN NOT ALSO BE A ISA SLOT. My Compaq 5152's board has a slot that can be a PCI or ISA slot. This is what caused my original problems with setting up this modem. Simply removing the card from the PCI/ISA slot and placing it into a STRICTLY PCI slot solved the problem of my I/O errors during my original setting up of this modem. This is the only help I have for solving the I/O errors that you might recieve during the setup of this modem.]

Select /dev/ttyS3 as the device in whichever dial-up communication program you're using. It should now initialize and operate.

Edit the rc.local or rc.serial file located in the /etc/rc.d directory. Add the two setserial lines at the end of the file. Save and reboot the system.

THE ABOVE WORKS FOR CALDERA OPEN LINUX 2.3 WHEN YOU HAVE AN ACTIONTEC
INTERNAL 56k PCI CALL-WAITING MODEM.

THE FOLLOWING ARE ADDITIONAL INSTRUCTIONS FOR OTHER DISTRIBUTIONS OF
LINUX(OTHER THAN CALDERA).

If you are using the S.u.S.E distribution, this can be done by adding the command to /sbin/init.d/serial  according to your needs.

If you are using Debian distribution, go to the /etc/rcS.d directory. Edit
the file called S30setserial (in Dapper=/etc/rcS.d/S30etc-setserial) and add the two setserial lines.[/COLOR]

---

