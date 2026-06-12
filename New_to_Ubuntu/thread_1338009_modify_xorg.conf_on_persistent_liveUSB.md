---
title: "modify xorg.conf on persistent liveUSB"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by joe_newbie on 2009-11-26
I am trying to get the touchscreen working on an eeetop from a liveUSB (live USB session with persistent settings). If I can get it working well with Karmic i will do a proper install but...According to the docs included with the evtouch driver i need to add the following to my xorg.conf:

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection



However, when I look in /etc/X11/ there is no xorg.conf !!! 
And according to my /var/log/xorg.0.log, the settings x is using are from a "built-in configuration"  Is there a way to modify the built in configuration either temporarily for testing purposes or permanently, given that I have persistent setting enabled? 


Any help is greatly appreciated.

Joe

---

### Post by mikewhatever on 2009-11-26
Newer versions of Ubuntu don't rely on xorg.conf, but nothing stops you from creating it manually. Will it work? That depends on the options you put in.

---

### Post by joe_newbie on 2009-11-29
Just wanted to let people know that I have solved the problem by installing the new version of the evtouch driver. No need to modify (or create) and xorg.conf file.

Package for Karmic found here:

[https://launchpad.net/ubuntu/karmic/+package/xserver-xorg-input-evtouch](https://launchpad.net/ubuntu/karmic/+package/xserver-xorg-input-evtouch)

Joe

---

