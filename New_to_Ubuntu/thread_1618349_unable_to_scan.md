---
title: "unable to scan"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by manny43 on 2010-11-10
Hello

Ubuntu 9.10
MFC-440CN

Printing not a problem but xsane only detects webcam as a scanner device.
Packages installed:brother-lpr-drivers-bh7
                               brother-cups-wrapper-bh7
Am i missing scanner drivers?Thanks in advance for your help

---

### Post by Cheesehead on 2010-11-10
The packages brother-lpr-drivers-bh7 and brother-cups-wrapper-bh7 are both printer drivers.

So you might indeed need to download scanner drivers for the hardware.

---

### Post by bedihardeep on 2010-11-10
> **manny43 said:**
> Hello

Ubuntu 9.10
MFC-440CN

Printing not a problem but xsane only detects webcam as a scanner device.
Packages installed:brother-lpr-drivers-bh7
                               brother-cups-wrapper-bh7
Am i missing scanner drivers?Thanks in advance for your help

here are the scanner drivers you are looking for 
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)


here is another help page 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

good luck

---

### Post by manny43 on 2010-11-10
Thank you for helping.I did install driver but the only way i can scan is as follow: sudo xsane this is the only way scanner is detected if i open xsane from applications it only detects webcam.
Bus 001 Device 003: ID 046d:0802 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by manny43 on 2010-11-10
sudo lsusb
Bus 001 Device 003: ID 046d:0802 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f9:01af Brother Industries, Ltd MFC-440CN
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by manny43 on 2010-11-10
**1.** Open "/lib/udev/rules.d/40-libsane.rules" file.**2.**Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
  
  
  The lines to be added---------------------------              
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
       **3.** Restart the OS.This solved the issue

---

