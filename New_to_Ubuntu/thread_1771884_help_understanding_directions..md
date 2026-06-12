---
title: "help understanding directions."
date: 2011-05-30
forum: New to Ubuntu
---

### Post by christianshearer on 2011-05-30
Hi, I am running ubuntu 10.10, and I am trying to get my garmin GPS unit to be able to upload/download to my computer.  I think I have everything lined up right, and I think I even know what needs to be done, but I don't know how to follow these directions.  Can you help me by telling me exactly what I need to type into the Terminal to make the following work?   I am getting this from:
[URL="http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux"]
http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux[/URL]

I need to change the permissions, and to do that I need to do the following, but how?

> To fix device permissions, you need to tell the system to create the device files with the required permissions. The device files should be readable and writable by your normal user. On most recent distributions this is done by creating a udev rules file

On Debian 4.0 and Ubuntu 8.04 and later, the files should have the group ‘plugdev‘, and be readable and writable by that group. Create /etc/udev/rules.d/51-garmin.rules containing:

ATTRS{idVendor}=="091e", ATTRS{idProduct}=="0003", MODE="0660", GROUP="plugdev"

Note: plugdev is deprecated, so this solution could stop working at any time. See this comment on Launchpad. The solution is to update PolicyKit for GPS devices (see attachments here.

On Fedora 5 and OpenSUSE 10.1 and later, create /etc/udev/rules.d/51-garmin.rules containing:

SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="0666"

Note: This tells udev to make the device files world readable

    FIXME: Needs confirming. Also, the mode seems awfully permissive: Can it be changed to match the Debian example?—Sward 22:35, 28 December 2008 (UTC) 

Load the new rule by executing:

sudo udevadm control --reload-rules

Disconnect and re&#8208;connect your GPS device, and check the permissions of the device files (the bus and device numbers may have changed).

Thanks for any help.

---

### Post by jtarin on 2011-05-30
This will be a little more graphical.
In a terminal issue the command ```
gksudo gedit /etc/udev/rules.d/51-garmin.rules
``` Then copy and paste the rule and Save.```
ATTRS{idVendor}=="091e", ATTRS{idProduct}=="0003", MODE="0660", GROUP="plugdev"
``` 
Then make your way to that file and right-click for properties and change the properties accordingly as it states. 
Then in a terminal Load the new rule by executing:```
sudo udevadm control --reload-rules
```

---

