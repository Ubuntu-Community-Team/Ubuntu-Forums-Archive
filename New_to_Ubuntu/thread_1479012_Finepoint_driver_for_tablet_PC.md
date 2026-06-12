---
title: "Finepoint driver for tablet PC"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Ronin51 on 2010-05-10
I posted a similar message last night, but I have a bit more information and this may be a more appropriate forum.

I just loaded ubuntu 10.04 on my Gateway CX210 Tablet. The OS works great, but the tablet functions/pen do not work. I found a fair amount of older, rather complex information about getting the tablet functions to work with a Linux based system. I hoping for something newer and maybe simpler. 

I did find out that Finepoint and its parent company Inplay appear to have been fully liquidated earlier this year. So there appears to be no chance of direct support. 

I'd like to get the tablet working, but I probably would not go back to Windows to do it. However, any help or suggestions would be greatly appreciated. 

BTW: can I safely assume simply loading the Finepoint driver from someplace like CNET will not fix the problem?

GB

---

### Post by Favux on 2010-05-10
Hi Ronin51,

I answered you on your other thread and linked you to the new finepoint driver for Lucid.

---

### Post by bornagainlinux on 2010-05-10
I also have a Gateway CX200X and since I have had Ubuntu 9.10 installed, I could not get the tablet to work. That would be great if I can get it working. I recently upgraded to 10.04 and I am getting used to it. I am not a new computer user. I have been using PCs and Macs for a long time. I am just getting used to Linux and understanding how it works. I learn best from examples. And I have looked around for help, but most of the time the help is very cryptic to me. 

Thanks in advance for all your help and patience.

Don

---

### Post by Favux on 2010-05-10
Hi Don,

Welcome to Ubuntu forums!

They just built fpit, the driver, for Lucid (and X server 1.7).  I don't think it's in the repositories yet.  So see my post here:  [http://ubuntuforums.org/showpost.php?p=9271187&postcount=2](http://ubuntuforums.org/showpost.php?p=9271187&postcount=2)

With luck the package will also include the configuration files and to get your tablet pc working you'll just need to reboot.

---

### Post by bornagainlinux on 2010-05-10
Thank you Favux, 

So do I just install just the fpit driver or do I need to also install the server-xorg file as well? Again thanks for the help.

Don

---

### Post by Favux on 2010-05-10
Hi Don,

The xserver-xorg-input-fpit package is the fpit driver.  Is that what you're asking?  That's just the name Ubuntu is using for it.

---

### Post by bornagainlinux on 2010-05-11
Hi Favux,

The other package I was asking about is named: xorg-server-2:1.7.6-2ubuntu7~xup2
This was listed along with xserver-xorg-input-fpit_1.3.0+git20100504.a7e1d84c-0ubuntu0sarvatt_i386.deb. 

I am also reading the posts from a similar topic on getting the tablet working. If the xorg-server package is not needed then I will follow the other topic.

Thank you,

Don

Update:

I have the tablet working. Well sort of. Here is what I did:

1) I installed the latest fpit driver as suggest previously. Rebooted and nothing worked.

2) I found in another forum post (and I cannot remember where I found it) posted by Favux that is the xorg.conf file. Here is what it contains:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Finepoint Tablet"
    Driver        "fpit"
    Option        "Device"        "/dev/ttyS0"
    # "BaudRate" may need tweaking (9600, 19200, or 38400).
#    Option        "BaudRate"        "19200"
    # For a passive pen, e.g. Stylistic 3400 use "true".
    Option        "Passive"        "false"
    # To make the touchscreen respond automatically to
    # resolution changes and screen rotation:
    Option        "TrackRandR"
    # Not sure if "SendCoreEvents" line is necessary.
    Option        "SendCoreEvents"    "true"
#    Option        "Buttons"        "2"
    # not sure which button line works or both together?
#    Option        "Button2"        "3"
    # These may need tweaking.
    Option        "MaximumXPosition"    "12550"
    Option        "MaximumYPosition"    "7650"
    Option        "MinimumXPosition"    "400"
    Option        "MinimumYPosition"    "400"
    Option        "InvertY"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
#    Identifier    "Default Layout"
#    Screen        "Default Screen"
    Inputdevice    "Finepoint Tablet"
EndSection

#
# Developed and tested with jrozo17 on a Gateway CX2724.
#
```Since the xorg.conf did not exist in /etc/X11 I created a new one in the terminal with
```
gksudo gedit /etc/X11/xorg.conf
```and pasted the above into it and saved it. Rebooted and it worked but the cursor jumped all over the place.

3) In a previous post it was stated that the baud rate of the serial port need to be changed to 38400. So I edited the file /var/lib/setserial/autoserial.conf and changed the baud rate from 115200 to 38400 like this:
```
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 38400 spd_normal skip_test
```

It was also suggested that the file /etc/rc.local and add the following before "exit 0":
```
setserial /dev/ttyS0 autoconfig

setserial /dev/ttyS0 port 0x03f8 uart 16550A irq 4 baud_base 38400

```Rebooted and now it works...sort of. The stylus is recognized when it is close to the screen, however it tracks fine toward the left edge. It seems to get more off the more right I move it.

I hope this helps someone.

---

### Post by bornagainlinux on 2010-05-25
Good news all! 

I just downloaded the latest fpit driver from launchpad.net

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid")

After rebooting the stylus tracks wonderfully! But now comes the bad news. The click does not work. Sooooo close!!  But very cool! Anyone want to help me figure this out? 

Again thanks to all that reply!

Don

---

