---
title: "how to install serial mouse"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by degarb on 2010-12-13
I have a Logitech First/Pilot Mouse Serial (M34,M35,C43)

* Ubuntu 10.1 doesn't apparently know this animal out of the box.   I don't have spare USBs. So, is there some terminal command I can get and install the driver for this serial mouse?  (Perhaps, like my belkin wireless card driver, where I had to use the windows driver? Also note, I don't feel like popping twenty dollar bills at the machine to get it Ubuntu compatible at this time of year.)

*Also, how do you get around in UBuntu with no mouse?  Tabbing doesn't work very well, like in windows.

*How do you bring up a terminal with keyboard alone?

---

### Post by degarb on 2010-12-13
I haven't tried, but guess alt f2 brings up run.  But, I probably need terminal.

Alt f1 might bring up application menu, where possibly I can get a terminal.

Naturally, I would prefer to install the serial mouse over buying another hub + usb mouse + additional power strip + prozac for wife to put up with additional cords.

---

### Post by LinuxCharms on 2010-12-13
To open the terminal you do Applications > Accessories > Terminal
As for your problem I have no idea. xD

---

### Post by degarb on 2010-12-13
Googling, looks like others cannot get this logitech mouse to work.  No solution found yet.

A ton of windows drivers are available for free download, when I google it.

---

### Post by low_rider on 2010-12-14
Can't say that I know too much about your specific mouse, but you could try finding the serial port that you are connecting to in /dev.  the specific port would probably start with tty.  Printing out what is in there with tail -f would at least tell you if you're getting anything from the mouse at all.

---

### Post by chamira on 2010-12-14
Have you tried connecting a basic serial mouse to the ps/2 (serial) port and booting up?

You need to check if this is an incompatibility issue with that particular Logitech mouse or something wrong with the port.

---

### Post by degarb on 2010-12-14
> **chamira said:**
> Have you tried connecting a basic serial mouse to the ps/2 (serial) port and booting up?

You need to check if this is an incompatibility issue with that particular Logitech mouse or something wrong with the port.

I stole a ps2 mouse from a defenseless little 10 year old girl.  It works fine.  While the port and logitech works fine under windows, I suppose you are insinuating the port could have Ubuntu compatibility issues.

---

### Post by muut on 2010-12-26
I have been trying to find useful information on how to make a serial (standard MS Serial Mouse 2.0A) work in Ubuntu 10.04 - it is attached to a plain 9-pin serial port (COM1) but connected through an Omni View 4 port Belkin PC Port switch box. Works just fine in Windows. I tried the xorg.conf change in the SerialMouseHowto-Community Ubuntu Documentation but that did not work when using Ubuntu 9.10 so I updated to 10.04 and now find that '...HAL is now used and auto-detects devices...' - but - I cannot find any documentation on how to get a serial mouse to wok or any clues...

Can anyone help?

---

### Post by muut on 2011-01-01
While waiting (and hoping) for a reply to this problem in this forum I finally found the solution at:

[http://www.uluga.ubuntuforums.org/showthread.php?p=9188246](http://www.uluga.ubuntuforums.org/showthread.php?p=9188246)

Maybe it will help someone else... and a big thank you to oldspammer.

---

