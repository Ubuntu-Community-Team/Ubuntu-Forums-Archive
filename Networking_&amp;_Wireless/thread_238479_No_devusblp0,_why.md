---
title: "No /dev/usblp0, why?"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by craiger316 on 2006-08-17
I am trying to configure my printer using CUPS however when I use the admin page to add a printer it never gives me an option to use USB as the device port.

I checked /dev and there is no listing for usblpx, any idea why?

lsusb gives me this:
> lsusb
Bus 001 Device 005: ID 043d:003d Lexmark International, Inc. X83 Scan/Print/Copy
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Yet, ls *usb* in /dev shows nothing.

Any help would be greatly appreciated.  I've tried reconfiguring CUPS, and making sure "usb" was selected as a valid source for a printer, however that didn't do it.

Craig.

---

### Post by craiger316 on 2006-08-18
Had to write my own udev rule to get it, but I got it now.

Here is what I did:

1. excuted: lsusb 
which produced this output:
Bus 001 Device 009: ID 043d:003d Lexmark International, Inc. X83 Scan/Print/Copy
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
2. changed directory to /sys
3. executed: find . -name '*usb*' 
part of the output was:
./devices/pci0000:00/0000:00:07.2/usb1/1-1/usb_device:usbdev1.9
./devices/pci0000:00/0000:00:07.2/usb1/1-2/usb_device:usbdev1.3
4. took a guess that the 1.9 corresponded to my printer as lsusb listed it as Bus 1 Device 9
5. executed: > udevinfo -a -p /sys/devices/pci0000:00/0000:00:07.2/usb1/1-1 
which produced:
>   looking at class device '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1':
    KERNEL=="1-1"
    SUBSYSTEM=="unknown"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="8"
    SYSFS{bMaxPower}==" 48mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0001"
    SYSFS{bmAttributes}=="e0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="9"
    SYSFS{idProduct}=="003d"
    SYSFS{idVendor}=="043d"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="Lexmark X83 Scan/Print/Copy"
    SYSFS{speed}=="12"
    SYSFS{version}==" 1.10"


6. created a udev rule based on the idProduct and idVendor attributes, the rule read like this:
> BUS=="usb", SYSFS{idProduct}=="003d", SYSFS{idVendor}=="043d", SYMLINK+="lexmark_x83"
What this will do is a device plugged into the usb port will be queried for it's vendor/product number.  If it matches the rule, a symlink will be created in /dev called "lexmark_x83" which points to the physical usb bus it is attached ot.

7. typed: > sudo vi /etc/udev/rules.d/99-usbprinter.rules and pasted the above rule into it and saved it
8. restarted udev: > <pre>sudo /etc/init.d/udev restart</pre>
9. changed directories to /dev and made sure the lexmark_x83 symlink was present.
10. in the "add printer" wizard I added a new printer, picked a Lexmark printer driver (none existed for x83) that was close in model number.  I setup the printer as IPP, and used the following URI: usb:/dev/lexmark_x83
11. printed a test page, nothing happend, checked /var/log/cups and found these messages:
> E [17/Aug/2006:23:51:09 -0500] [Job 2] No %%BoundingBox: comment in header!
E [17/Aug/2006:23:51:20 -0500] [Job 2] /ioerror in --.outputpage--


Actually, there were a tonne of these as well:
cupsdAuthorize: Local authentication certificate not found!

Anywho, all that trouble just to find out that the Lexmark X83 cannot work with Cups/Linux.  There is no driver for it, and no compatible driver.

If it were me, I would probably buy a new printer, however [it's for my Auntie]("http://www.acmebinary.com/blogs/craiger/archive/2006/07/29/No_I_will_not_Fix_your_Computer.aspx") and she can't live without her colour all-in-1 X83.  So, I have to trash Ubuntu and throw XP back on.

---

