---
title: "need help with WiFi drivers"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by tsco59 on 2010-02-21
Yesterday installed Ubuntu 9.1 Karmic Koala on i386 machine.  This is my very first exposure to Linux.  

No WiFi was working so now trying to install drivers for USB Wireless D-Link DWA-130.  (I have proven XPpro .inf and .sys files.)

Plan A: found rtl8192u_linux driver ver 0.06 for 2.6 kernal.  ran scripts with many many errors. Didn't write 'em down and punted.  Reinstalled Ubuntu for a clean system.

Plan B: follow WifiDocsDriverNdiswrapper How-To.  So far...
B.1 installed 9.1 ndiswrapper-common, ndiswrapper-utils-1.9, ndisgtk using sudo dpkg -i and no errors
B.2 blacklisted: bcm43xx, b43, b43legacy, ssb, rt2500usb then rebooted
B.3 lsusb finds Bus 001 Device 002: ID 07d1 D-Link System Wireless N Adapter DWA-130
B.4 ran sudo ndiswrapper -i mrvw245.sys and got no errors.  (netmw245.inf was in the same directory)
B.5 Maybe Problem: ndiswrapper -l: "WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."  netmw245:driver installed   device (07D1:3B11) present
B.6 Maybe Problem: loading the "new driver module"
    - typed sudo depmod -a, hard drive got busy then terminal prompt - no messages
    - typed sudo modprobe ndiswrapper, returned same WARNING as above and a segmentation fault.
B.7 System/Admin now shows Windows Wireless Drivers in the drop down but clicking on it yields a msgbox: Unable to see if hardware is present.  Clicked OK and netmw245 is shown as Currently Installed.  Clicking the Configure Network button = msgbox: Could not find a network configuration tool.

So... WinXp is starting to look better to me but I'd like to think someone could teach this old dog a new OS.  Any suggestions?  (I expect once I have internet access I'll be much happier.)

---

### Post by themusicalduck on 2010-02-22
Have you tried going to System > Administration > Hardware Drivers to see if you can download a driver from there?

You'll need an internet connection to install it, so you might have to connect using an ethernet cable if you can.

---

### Post by k3lt01 on 2010-02-22
> **tsco59 said:**
> Yesterday installed Ubuntu 9.1 Karmic Koala on i386 machine.  This is my very first exposure to Linux.  

No WiFi was working so now trying to install drivers for USB Wireless D-Link DWA-130.  (I have proven XPpro .inf and .sys files.)

Plan A: found rtl8192u_linux driver ver 0.06 for 2.6 kernal.  ran scripts with many many errors. Didn't write 'em down and punted.  Reinstalled Ubuntu for a clean system.

Plan B: follow WifiDocsDriverNdiswrapper How-To.  So far...
B.1 installed 9.1 ndiswrapper-common, ndiswrapper-utils-1.9, ndisgtk using sudo dpkg -i and no errors
B.2 blacklisted: bcm43xx, b43, b43legacy, ssb, rt2500usb then rebooted
B.3 lsusb finds Bus 001 Device 002: ID 07d1 D-Link System Wireless N Adapter DWA-130
B.4 ran sudo ndiswrapper -i mrvw245.sys and got no errors.  (netmw245.inf was in the same directory)
B.5 Maybe Problem: ndiswrapper -l: "WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."  netmw245:driver installed   device (07D1:3B11) present
B.6 Maybe Problem: loading the "new driver module"
    - typed sudo depmod -a, hard drive got busy then terminal prompt - no messages
    - typed sudo modprobe ndiswrapper, returned same WARNING as above and a segmentation fault.
B.7 System/Admin now shows Windows Wireless Drivers in the drop down but clicking on it yields a msgbox: Unable to see if hardware is present.  Clicked OK and netmw245 is shown as Currently Installed.  Clicking the Configure Network button = msgbox: Could not find a network configuration tool.

So... WinXp is starting to look better to me but I'd like to think someone could teach this old dog a new OS.  Any suggestions?  (I expect once I have internet access I'll be much happier.)
This is what I do. Make sure you copy and paste each command as it is written, only change the xxxxxx.inf for your .inf file.
```
# Notes. Make sure drivers are visible on the Desktop then copy and paste each command into a terminal to install the wireless network drivers for the relevant wireless card.
# where xxxxxx is the name of your .inf file

cd Desktop

sudo ndiswrapper -i xxxxxxx.inf 

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```
Yes sometimes you will get a message but I have never had a failure doing this yet.

---

### Post by tsco59 on 2010-02-22
Thanks for the help.  I spent 30 minutes with some Cat5 and a pair of crimpers and ran a new line to the basement.  Now I'm wired and on-line so no need for wifi.  Hey, when the only tool you've got is a hammer, everything looks like a nail.  Thanks again.

---

