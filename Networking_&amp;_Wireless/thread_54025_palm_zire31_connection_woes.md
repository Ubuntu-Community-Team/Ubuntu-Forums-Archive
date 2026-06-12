---
title: "palm zire31 connection woes"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by casperl on 2005-08-03
hi all, 
I'm having problems getting the palm zire 31 to work with Ubuntu 5.04
I have followed the instructions in the ubuntu wiki:

[https://wiki.ubuntu.com/PalmZire31HowTo?highlight=%28palm%29](https://wiki.ubuntu.com/PalmZire31HowTo?highlight=%28palm%29)
and,
[https://wiki.ubuntu.com/EasyPalmDeviceSetup?highlight=%28palm%29](https://wiki.ubuntu.com/EasyPalmDeviceSetup?highlight=%28palm%29)
as well as
[http://ubuntuguide.org/#configurepalmosdevices](http://ubuntuguide.org/#configurepalmosdevices)

when I press the hotsync button on the palm lsusb reports:
Bus 001 Device 076: ID 0830:0061 Palm, Inc.
Bus 001 Device 001: ID 0000:0000

I have an /etc/udev/rules.d/10-custom.rules with the content:

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

I have added this line to  /usr/share/gnome-pilot/devices.xml

 <!--Palm Zire 31-->
  <device vendor_id="0830" product_id="0061" />
  
Pressing the hotsync button on the Zire 31 (connected to the USB cable) shows the following device in /dev/

casperl@fiela:/dev$ ls -la pilot
crw-rw-rw-  1 root root 188, 0 2005-08-03 09:39 pilot

This device disappears when the hotsync button is not pressed on the palm

Gnome-pilot is set to Cradle / /dev/pilot / 115200 / 2 / UBS

Still no hotsync, no response.

BTW, the USB link works, a MMC card reader shows up straightaway as a removable device.

Any suggestions????

---

### Post by casperl on 2005-08-03
Update to above ...

After the Palm Zire 31 has been disconnected the following is reported:

casperl@fiela:/dev$ ls -la pilot
ls: pilot: No such file or directory
casperl@fiela:/dev$ lsusb
Bus 001 Device 001: ID 0000:0000

Connecting the Palm Zire 31 and starting hotsynch the following is reported:

casperl@fiela:/dev$ ls -la pilot
crw-rw-rw-  1 root root 188, 1 2005-08-03 11:39 pilot
casperl@fiela:/dev$ lsusb
Bus 001 Device 089: ID 0830:0061 Palm, Inc.
Bus 001 Device 001: ID 0000:0000

BTW I have also killed the pilotd daemon (ps -A | grep pilot ; kill [pid]) after major changes and restarted ubuntu twice in the past weeks.

It looks to me as though ubuntu works ok, the problem has to be something so obvious that I cannot spot it.

TIA

---

### Post by casperl on 2005-08-03
Update #3

The palm zire 31 now talks to ubuntu!

I enabled everything in synaptic for the Palm and installed it.

The zire came to life, and hotsynch completed after I instructed the s/ware to check the correct user ID from the device.

The new s/ware looks entirely different from the previous under Gnome > System > Preferences > Palm OS Devices

Hope this helps someone else!

---

