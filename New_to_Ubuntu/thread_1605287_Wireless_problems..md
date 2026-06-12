---
title: "Wireless problems."
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Hodgeboy on 2010-10-25
Pardon me if I'm missing something simple, but I'm not the greatest when it comes to computers and I heard that ubuntu was becoming much more user friendly. The problem I'm currently having is that my desktop has a built in wireless card which I promptly don't use (Because its ****). But I instead use a usb wireless card to connect to the internet. Well, anytime that I boot into Ubuntu (Using Wubi) it won't use my usb card, but instead the machine's default. Any help with this? Because accessing the internet is so slow that its becoming quite frustrating. Thanks for your time.

---

### Post by Hippytaff on 2010-10-25
does ubuntu see the usb wireless dongle? might need a bit of configuring. In a terminal (CTRL+ALT+T) type
```

lsusb

```
while the usb dongle is in
and post the output

---

### Post by Verbeck on 2010-10-25
when you click the network manager applet doesn't it show the two adapters?

[IMG]http://i55.tinypic.com/x1kj9i.jpg[/IMG]

---

### Post by Hodgeboy on 2010-10-25
This is what it says when I typed the command into terminal.

Bus 002 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 15a9:0004  
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 1385:4251 Netgear, Inc WG111T (no firmware)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Hippytaff on 2010-10-25
> 
Bus 001 Device 003: ID 1385:4251 Netgear, Inc WG111T (no firmware)


you probably need to install the driver/module WG111T

[https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)

---

### Post by Hodgeboy on 2010-10-25
Going to give it a shot. As previously stated I'm not super tech savvy, but will let you know how everything works.

---

### Post by Hodgeboy on 2010-10-25
Hmm, I've just got to be doing something wrong. I read up on what to do, and still back to square one.

---

### Post by Verbeck on 2010-10-25
[http://ubuntuforums.org/showthread.php?t=1577023](http://ubuntuforums.org/showthread.php?t=1577023)

 see post #2 . it solved the issue for the OP (same adapter model)

---

### Post by Jose Catre-Vandis on 2011-01-16
Here is link to the driver files needed for WG111T

```
http://hotfile.com/dl/97241482/faa2e6f/WG111t-Driver.tar.gz.html
```

---

### Post by wep940 on 2011-01-16
Since 1 of the threads mentioned above suggests using the Windows driver for your adapter via ndiswrapper, be aware that many of the ndiswrapper how-to's out there are outdated and have you do unneccesary things.  Just do the following:
[LIST]
[*]After booting Ubuntu, insert the LiveCD and let it spin up.  If you get a message about a software source being found just cancel it.
[*]Using "Places", navigate to the /pool/main/n/ndiswrapper folder on the CD.
[*]Double-click the ndiswrapper common file to install it - wait for the installation to finish.
[*]Double-click the ndiswrapper utilities file to install it - wait for the installation to finish.
[*]Navigate to the /pool/main/n/ndisgtk folder on the CD.
[*]Double-click the ndisgtk file to install it - wait for the installation to finish.  ndisgtk is a GUI'd front end to ndiswrapper and makes things much easier.
[/LIST]That finished installing the programs.  Next you need to copy the driver files for your adapter (the .inf and .sys files) to your desktop.  Note that these drivers can only be Windows XP drivers, and the architecture must match the OS architecture - 32 bit drivers for 32 bit Ubuntu, 64 bit drivers for 64 bit Ubuntu.
 
Now to install the drivers:
[LIST]
[*]Go to System/Administration/Windows Wireless Drivers and click.  This will start up ndisgtk.
[*]Click on the "new..."  or "add..." (I'm in Windows right now so I don't remember the exact wording).
[*]Point it to the .inf file for your driver and click "add...".
[*]You should now see the device/driver as active.
[/LIST]Other things to remember:
[LIST]
[*]If the router is using MAC filtering, be sure the adapter's MAC address is in the allowed list on the router.
[*]If the router is using encryption, you must match the type and the password/passphrase.
[*]If the router is not broadcasting the network name you must go through network manager and select "Connect To Hidden Network".
[*]Right-click on the network manager icon and be sure "Enable Wireless" shows and be it is enabled.
[*]Left-click on the network manager icon to see if wireless networks are now being found.
[/LIST]

---

