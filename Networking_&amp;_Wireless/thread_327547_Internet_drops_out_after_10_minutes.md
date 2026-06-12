---
title: "Internet drops out after 10 minutes"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by themusicwave on 2006-12-29
I'm having a strange and annoying problem.  WHen using my computer, whihc is a Dell inspiron E1505, my internet drops out after about 10 minutes.

This happens on both my wireless connection and my ethernet connection.  The strange part is, the computer still says it is connected.  However, if I try to load a webpage it times out or the is unable to connect.

This happens on both linux and windowx xp(sorry I need it for school...).  I have no idea whats wrong and it is driving me crazy.

I tried calling Dell, but they are not much help since when I installed Ubuntu I overwrote the diagnostic partition on the drive.

The only thing I can think of is that I ran a MAC shifter on Windows, I needed to access the internet in a computer lab, which required a set MAC.  I beleive I shifted the MAC back to normal when I was done though.

Any help would be great, thanks!

---

### Post by Iowan on 2006-12-29
Were it not also happening on the Windows box, I'd be thinking **dhclient** was causing issues.

---

### Post by handy on 2006-12-30
Try having a look at your router's firmware settings?

**Idle Timeout** value?

Best I can do for you, your problem would seem to be in the router not your operating systems, if windoze & linux share the same problem?

---

### Post by Mark_in_Hollywood on 2006-12-30
This post is unlikely to be any help to you, but I'm putting it here, because I have a similar problem with dial-up. After 6 months of this, I believe I may have found a solution and yours could be similar, I'm not into computers enough to program, etc., I just follow the instructions others have posted, here - there - everywhere.

[COLOR="Blue"]Okay, the modem in question is the 3Com/USRobotics 3CP5610 PCI FaxModem.  It is one of the few PCI modems that is controller based, having an on-board 16550AF chip.  It is a K56 flex V.90 modem, which works very well for me.  The greatest problem that people have with this modem is that it installs on COM5 in Win9* and there is no com5 (by default) in linux.

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
the file called S30setserial and add the two setserial lines.

======================================================

is there a command which terminates the modem?
I tried sudo killall, to no success
======================================================



mark@Lexington:/dev$ sudo setserial /dev/ttyS4 port c800 spd_vhi skip_test auto_irq autoconfig
mark@Lexington:/dev$ setserial /dev/ttyS4 uart 16550A


System/Administration/Device Manager shows:
16550A-compatable com port | key is: info.udi
                             type is: strlist
                             value is: /org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0

linux.device_file strlist /dev/ttyS0


Venus Modem                | key is: info.udi
                             type is: strlist
                             value is: /org/freedesktop/Hal/devices/pci_11c1_480_serial_platform_4

linux.device_file strlist /dev/ttyS4[/COLOR]

---

### Post by themusicwave on 2007-01-03
I think it might be the router, but am still not sure.  I spent 4 hours on the phone with Dell tech support today and still nothing.

We ran some diagnostics and all the hardware checks out fine.  So I am guessing I messed up the router setup. Looks like I will have to spend some time talking to linksys tech support..........

---

