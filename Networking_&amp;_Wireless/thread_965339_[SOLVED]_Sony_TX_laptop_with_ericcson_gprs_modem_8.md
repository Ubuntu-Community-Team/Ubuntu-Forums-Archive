---
title: "[SOLVED] Sony TX laptop with ericcson gprs modem: 8.04 method not working"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by sheaiden on 2008-10-31
OK, 8.10 is out, and I desparately want to upgrade, since it uses the new version of mesa and wine, and my intel 915 graphics don't play well with the 8.04 version.  In addition, I've heard that Ibex is supposed to be very friendly to laptops connecting using wwan cards, like mine.

But...

I am having the an issue with getting my Sony Vaio TX750P's Ericcson AB VDC EGPRS modem working.  I had issues with this in 8.04, and nothing has ever tasted as sweet as the victory I felt at finally getting it to work, but the same procedure seems not to work with 8.10.  

Here's what I did to get it working in 8.04:

It's a sony, so to turn on the gprs modem, you have to do:
```
echo "1" > /sys/devices/platform/sony-laptop/wwanpower
```

wwan module is now turned on.  I had udev rules set up tomake sure it always got the same device name:

/etc/udev/rules.d/55-gprs.rules
```
BUS=="usb", SYSFS{idVendor}=="0fce", SYSFS{idProduct}=="d019", NAME="gprs_modem", GROUP="dialout", RUN+="/etc/udev/scripts/gprs_modem_setup.sh"
```
And then this is the script udev executes:

/etc/udev/scripts/gprs_modem_setup.sh
```
#!/bin/bash
/bin/echo -en "AT+CFUN=1,1\r\n" > /dev/gprs_modem
```

from here, I would execute gprsec and use that to connect.

I copied the rule and script to my 8.10 partition from my 8.04 (I'm not replacing 8.04 till I verify I can connect with 8.10).

Now, that being said, here's the error I'm getting in 8.10:

before leaving it all up to scripting, I decided to try getting this working manually, so I:

1: turned on the modem 
2: watched in the message log as it saw the usb device,
3: checked in /dev and saw the /dev/gprs_modem device appear
4: Tried to echo the string to the device, but get this error: 
```
-su: /dev/gprs_modem: No such device or address
```

nothing further shows up in the logs.  I've tried tracking syslog, udev, kern, messages, and more, but other than the "USB device connected, using profile 1" (paraphrased) message that it shows up for every usb device you plug in, there's nothing.  

I even tried taking out the udev stuff, and just using the regular devices it creates, but all of them give the same error.  it always creates 4 entries when I don't have the udev rule in place, along the lines of /dev/usbdev4.2_ep00, ep02, ep81, and ep82.  the device number changes at times (4.4, 5.1, etc...) none of these entries appear when I have the udev rule in place, the only entry that appears is gprs_modem.  

what does this mean when it says no device?  I would think that when it creates the device entry in /dev, it would see a device...Do I need to do a different kernel in this version that I didn't in the previous?  is there a driver turned off here?  are there extra things in the DVD version that are missing in the CD version that would help me out here?

I have a fresh install of 8.10, as it has taken over 20 minutes so far to update the package databse in synaptic...I will try running an update and then trying again, but I don't know if that will work.

And, once I get it turned on and initialized, is gnome's nm supposed to just see it and give me an option to connect to the mobile broadband connection I already defined in nm's "Edit connections > Mobile broadband" tab?  How does that work?  I've not stumbled across the documentation on how thats supposed to work now.  it would be nice if I didn't need to install or run gprsec...

---Edit----
Some additional info.  I got cu installed, and tried to do a "cu -l /dev/gprs_modem", but got:
```
cu: open (/dev/gprs_modem): Permission denied
cu: /dev/gprs_modem: Line in use
```

Keep in mind, this is after doing a "sudo su -", so I am executing this as root.  How do I determine what's going on here?  something's using the line?

---Edit 2----
I have now checked with gprsec, and it can't access the modem, suggests I have not initialized it.  I have also done an update, and am fully up to date.  All in all, it looks like I have to figure out why I can't initialize the modem (the "echo AT+..."etc. portion from above).  any ideas?

---

### Post by sheaiden on 2008-11-03
no one knows why it would make the device entry in /dev, but be unable to communicate to the device?  It's recognized in lsusb, do I have to make a custom kernel?  Is there some sort of driver that I have to install in 8.10 that I didn't in 8.04?  what could have made the change from 8.04 to 8.10?

---

### Post by sheaiden on 2008-11-03
I found the output from lshal that pertains to my modem.  here:

```
udi = '/org/freedesktop/Hal/devices/usb_device_fce_d019_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.product = 'VDC EGPRS Modem'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_fce_d019_noserial'  (string)
  info.vendor = 'Sony Ericsson Mobile Communications AB'  (string)
  linux.device_file = '/dev/bus/usb/004/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 514  (0x202)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1'  (string)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'VDC EGPRS Modem'  (string)
  usb_device.product_id = 53273  (0xd019)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Sony Ericsson Mobile Communications AB'  (string)
  usb_device.vendor_id = 4046  (0xfce)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_fce_d019_noserial_if0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_fce_d019_noserial'  (string)
  info.product = 'USB Vendor Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_fce_d019_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 514  (0x202)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0'  (string)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.product_id = 53273  (0xd019)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Sony Ericsson Mobile Communications AB'  (string)
  usb.vendor_id = 4046  (0xfce)  (int)
  usb.version = 1.1 (1.1) (double)

```

Any idea why it says noserial in the beginning?  wouldn't it need to be able to work serially?  also, since /dev/gprs_modem appears when I turn on the modem, why would it show the path as /dev/bus/usb/004/002?  I'm a little out of my depth when it comes to devices and the underlying recognition of hardware in Linux....it's kind of like cars-I know how to fix what I've had to fix before, and I can research if I know what to look up...but I'm stumped here.

---

### Post by sheaiden on 2008-11-03
Upon further research, it appeared there was a step I was missing; I added the usbserial module to my /etc/modules, but I didn't specify the vendor or product id in the line.  

I have now gotten a ttyUSB0 device (without the udev rule) and have tested communication to the device (the echo "AT..." line).  

I have not been able to get anything new to appear in the gnome netework manager applet yet, and I've not been able to test the gprsec method (which I was using in the 8.04) because I've managed to screw up permissions in all my tinkering.  

I am considering this solved, and I'll open threads on the network manager issue if I can't find anything about it in the forums.

Thanks for at least looking at this...

---

