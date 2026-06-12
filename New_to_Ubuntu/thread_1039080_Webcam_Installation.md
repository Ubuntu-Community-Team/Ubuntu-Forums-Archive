---
title: "Webcam Installation"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Warpnow on 2009-01-14
Bought a Gear Head Webcam and am trying to install it with no luck. 

The guide said to type ls /dev/video*, but that command returns

chase@chase-desktop:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
chase@chase-desktop:~$ 

Has the mounting point of video devices changed in recent releases?

---

### Post by PriceChild on 2009-01-14
Could you paste the output of ```
lsusb
```please?

---

### Post by Warpnow on 2009-01-14
kchase@chase-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 093a:2620 Pixart Imaging, Inc. 
Bus 004 Device 002: ID 046e:5250 Behavior Tech. Computer Corp. KeyMaestro Multimedia Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:7e04 Hewlett-Packard Deskjet F4100 Printer series
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chase@chase-desktop:~$

---

### Post by RichardLinx on 2009-01-14
Not sure if this will help or not but I'll throw it out there anyway... You could try installing Cheese, It might be able to detect/configure your camera.

---

### Post by PriceChild on 2009-01-14
[http://ubuntuforums.org/archive/index.php/t-900250.html](http://ubuntuforums.org/archive/index.php/t-900250.html) is a good read from August, someone was able to get images from the webcam but not complete success with video. It seems as though work was going into the gspca driver to support it but evidently it doesn't atm. Not sure what to suggest yet I'm afraid but more googling.

---

### Post by PriceChild on 2009-01-14
> **RichardLinx said:**
> Not sure if this will help or not but I'll throw it out there anyway... You could try installing Cheese, It might be able to detect/configure your camera.hehe can't hurt... ```
sudo apt-get install cheese
```Although if there's no /dev/video0 then I don't think its going to help :/

---

### Post by Warpnow on 2009-01-14
Installing cheese was the first thing I tried, and it didn't work.

Hrm, this seems really complicated for something so simple as capturing an image from a camera.

---

