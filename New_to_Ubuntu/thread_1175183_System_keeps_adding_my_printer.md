---
title: "System keeps adding my printer"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by JEStone on 2009-05-31
I'm having all kinds of problems trying to ad my HP Laserjet 1500L. Ubuntu 9.04 keeps adding the printer to the system. Laserjet 1500, Laserjet 1501, laserjet 1502, etc... and printing endless amounts of test prints.

I'm a absolute beginner. Is there a simple solution for this or do I need to move the printer to the kids room and use XP printer share?

Please help.

---

### Post by keplerspeed on 2009-05-31
I have HP laserjet 1020. Might be able to help you.

Does your computer add a new printer if you turn the printer off, then back on? Similar on a reboot?

How did you initially add the printer? Did you plug in the usb and it was detected automatically?

For my laserjet, I got it working well by adding the printer with this command:

```

sudo hp-setup -i

```

And selecting all the defaults. However, my printer must be turned off when booting, otherwise it stuffs up and adds a new printer, using the generic driver.

---

### Post by OutOfReach on 2009-05-31
Do you plug in the printer into a different USB port each time?

---

### Post by JEStone on 2009-06-01
keplerspeed

I've tried your solution, but still no luck.

Is there a way to stop ubuntu from automatic adding printers?

---

### Post by cariboo on 2009-06-01
Are you using System-->Administration-->Printing to setup the printer? The printer will be auto detected, so just add the printer and you should be ok.

---

### Post by JEStone on 2009-06-01
The issue I'm having is that ubuntu is auto detecting the printer every 2 mins as a new printer. IE: Laserjet 1500, two mins later it adds Laserjet 1501, two mins later it ads Laserjet 1502, etc.. same printer in the same USB port.

---

### Post by LewRockwell on 2009-06-01
it sounds like it's auto-detecting but then not properly installing the printer.

just an idea, but have you tried a different cable to the printer?

in the past I have had weird issues with bad cables.

and you'll probably need to remove the printer, uninstall, reboot, reconnect, and re-install

whew...

wheeeee....

---

### Post by JEStone on 2009-06-06
Solved

After thinking about a bad USB cable I checked the USB on my old laptop. Its a USB 1.0 and the printer is USB 2.0. 

today I bought a PCMCIA usb hub and everything is working great! 

thanks for the support.

---

