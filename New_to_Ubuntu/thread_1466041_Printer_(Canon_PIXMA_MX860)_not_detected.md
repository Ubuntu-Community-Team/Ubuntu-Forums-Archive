---
title: "Printer (Canon PIXMA MX860) not detected"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by llmunro on 2010-04-29
Hi,

On to the next problem!  :)

I've installed the printer drivers from the Canon Europe site, but my printer is not detected, for some reason.  It is on an connected, but in the printer menu (Administration>printing), there's no option to add it, as that option is grayed out and at the bottom, the box says, "not connected."

How should I proceed?

Thanks much!
Best,
Lisa

---

### Post by madjr on 2010-04-30
same happens on mac

canon is not very friendly to mac or linux (but linux does have more support so some could work)

you can read more here:

[http://www.mac-forums.com/forums/os-x-applications-games/165494-printer-drivers-mac.html](http://www.mac-forums.com/forums/os-x-applications-games/165494-printer-drivers-mac.html)

[http://ubuntuforums.org/showthread.php?t=1397864](http://ubuntuforums.org/showthread.php?t=1397864)

Hp printers are the best multi platforms and detected automatically

sorry i wished i could be of more help :(


edit: ok i saw your other thread
[http://ubuntuforums.org/showthread.php?t=1463237](http://ubuntuforums.org/showthread.php?t=1463237)

so this means it was working and then stopped working?

---

### Post by llmunro on 2010-04-30
Well, here's what happened.  I installed the RC of 10.04 and Ubuntu automatically detected my printer, but then proceeded to do wacky, wacky things, like refuse to shut down or reboot. There was also a bizarre problem of a complete freeze up that I couldn't resolve. Alarmed by this and not having any real idea how to fix it, I reinstalled 10.04. (Drastic, perhaps, but it solved these problems!)  It is now working fine, but hasn't detected the printer.

Although Linux and Canon don't tend to get along, the printer has worked before.  I've no doubt that I'm just overlooking some sort of obvious, little, but crucial thing.

Thanks much.
Best, 
Lisa

---

### Post by madjr on 2010-04-30
ok so ubuntu rc, began doing wacky things :P


[http://forums.linux-foundation.org/read.php?25,9006,11881](http://forums.linux-foundation.org/read.php?25,9006,11881)

> Re: Canon PIXMA MX860 All-in-One
Posted by: Elise B. Hernandez (IP Logged)
Date: August 04, 2009 10:56AM

Linux drivers are available from Canon for both printing and scanning with the PIXMA MX860.

Download the drivers from the Canon Europe website:
[software.canon-europe.com]

Select "Linux" as the operating system, and then your language, from the pull-down menus, then click 'Submit'. You will see Linux drivers named "Printer Driver" for printing, and "ScanGear MP" for scanning. Drivers are available in Debian package (.deb) or RPM (.rpm) format.

After you've installed the drivers, plug in your printer (via USB) and configure it to use the 'cnijusb:' (not the 'usb:') device URI.

Printing and scanning both work for me, on Ubuntu.

more people with canon printers:
[http://ubuntuforums.org/showthread.php?t=1377309](http://ubuntuforums.org/showthread.php?t=1377309)

fedora how to (similar to ubuntu i guess):
[http://mairin.wordpress.com/2010/01/17/how-to-set-up-the-canon-pixma-mx860-wih-fedora/](http://mairin.wordpress.com/2010/01/17/how-to-set-up-the-canon-pixma-mx860-wih-fedora/)


anyway i recommend you open a bug report at [https://launchpad.net/](https://launchpad.net/)
if it was working, then they have to help fix it for you and make sure it stays working in future releases/updates :)

---

### Post by llmunro on 2010-04-30
Here's something mysterious...

The printer has magically reappeared in the Printer box!  How and why, I can't quite say, but it appeared without any intervention on my part!

Solved!

:D

Thanks for all the suggestions!

Best,
Lisa

---

