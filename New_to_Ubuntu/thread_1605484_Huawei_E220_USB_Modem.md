---
title: "Huawei E220 USB Modem"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Free Diver on 2010-10-25
Hi All
 
Today I started using Linux for the first time. I have installed linux onto our computer and when it starts up it gives me a choice to use windows or linux. The problem is that I can't connect to the internet when in Linux. I am connecting through Telkom using a Huawe E220 USB Modem. The modem program 'mobile connect' is in the E220 USB modem so when you are in windows and you plug in your modem, the modems program automatically installs itself and all you have to then do is put in your password and connect to the internet. Everything is configured for you automatically.
 
When I am in Ubuntu version 10.10 though and I plug in my Huawe E220 USB modem, Ubuntu doesn't automatically recognize my modem software and can't connect to the internet. Is there an easy simple way to connect to the internet using Ubuntu Linux?
 
Any help would be appreciated! Today is very first time using Linux and I can't code. :)

---

### Post by C.S.Cameron on 2010-10-25
I recall that I plugged in the modem,
went to Network Connections / Mobile Broadband / Add / Select Providers Country / and then select my provider from the drop down list.
And it worked without installing anything.

---

### Post by fandango11 on 2010-10-25
worked for me too.....no problem

---

### Post by thavinci on 2010-12-22
Any advise, does not pick up at all my side with 10.10 i386

The CD-Rom Mass Storage gets picked up by system but not modem side.

gnome-ppp does not pick anything up nor anything in Mobile Broadband Under Network Connections.....

---

### Post by Sealbhach on 2010-12-22
Try configuring it with Gnome-PPP using the wvdialconf command:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#For%20Ubuntu,%20alternative%20approach%20%28using%20gnome-ppp%29](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#For%20Ubuntu,%20alternative%20approach%20%28using%20gnome-ppp%29)

Normally, as you probably know, this E220 modem works out of the box.

.

---

### Post by thavinci on 2010-12-23
/dev/modem doesn't exist so can't do command line approach.


I have looked at dmesg and i cannot see any modem/serial driver attaching to this device. Only the Mass Storage CDROM Driver.


It's as if Ubuntu is not detecting the modem side of the device.

---

### Post by madmax75 on 2010-12-23
Are you using 10.04 or 10.10?  

I believe 10.04 didn't come with the **usb-modeswitch** and the **usb-modeswitch-data** packages. 

You need those to switch the modem from storage mode to modem mode.  

I think 10.10 should have them as a default?

---

### Post by thavinci on 2010-12-23
I'm using 10.10....
But i will check for those packages...


Just FYI, i have same issue with a PCMCIA HUAWEI E620 card

---

### Post by thavinci on 2010-12-23
An update....

Those packages are installed and i had to do some research as to how to use them.

lsusb result:
```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

So i ran
sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1003

Which presented me with:
```
Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 No devices in default mode or class found. Nothing to do. Bye.


```

So i eventually modifed /etc/usb_modeswitch.conf as follows:
```
# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0

DefaultVendor=0x12d1
DefaultProduct=0x1003

# TargetClass=0xff

CheckSuccess=20

HuaweiMode=1


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>"

EnableLogging=0


```

Which is based on the original with the exception that i commented out the TargetClass

This gave me  result:
```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf 

Note: target parameter missing; success check limited
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 007 on bus 003 ...
Using endpoints 0x02 (out) and 0x82 (in)
Using endpoints 0x02 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technologies
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent

Checking for mode switch (max. 20 times, once per second) ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Original device still present after the timeout

Mode switch most likely failed. Bye.

```

And as it states it failed as watching /var/log/messages shows device is still in mass storage mode and never changes....

So at least we onto something here, however it doesn't work "out the box" :p

Any advice as too where from here?

---

### Post by gandaran on 2010-12-23
> **thavinci said:**
> An update....

Those packages are installed and i had to do some research as to how to use them.

lsusb result:
```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

So i ran
sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1003

Which presented me with:
```
Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 No devices in default mode or class found. Nothing to do. Bye.


```

So i eventually modifed /etc/usb_modeswitch.conf as follows:
```
# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0

DefaultVendor=0x12d1
DefaultProduct=0x1003

# TargetClass=0xff

CheckSuccess=20

HuaweiMode=1


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>"

EnableLogging=0


```

Which is based on the original with the exception that i commented out the TargetClass

This gave me  result:
```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf 

Note: target parameter missing; success check limited
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 007 on bus 003 ...
Using endpoints 0x02 (out) and 0x82 (in)
Using endpoints 0x02 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technologies
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent

Checking for mode switch (max. 20 times, once per second) ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Original device still present after the timeout

Mode switch most likely failed. Bye.

```

And as it states it failed as watching /var/log/messages shows device is still in mass storage mode and never changes....

So at least we onto something here, however it doesn't work "out the box" :p

Any advice as too where from here?
is your modem the e220? the huawei e220 is one of the best supported modems on ubuntu. you don't have to do anything on ubuntu 10.10 except run the network manager » mobile broadband setup wizard and choose country and internet provider (just ensure the the internet provider APN is correct) thats all, anything else you do just mite complicate things.

---

### Post by thavinci on 2010-12-23
Yes it is the E220....

I followed that procedure initially but did well nothing at all...


I just sit with a profile that lists "Last Used" Never...

And when i add the profile, on the first screen where you can select mobile broadband device, well you cannot select the device and is grayed out as "Any Device" which leads me to think it doesn't pick device up....

gnome-ppp scan also does not pick up modem...

---

### Post by thavinci on 2010-12-23
Ok i have finally solved it!

First i Tried a HUAWEI E620 card aswell which also didn't work.
Then I tried a Vodafone Option Qualcomm 3G CDMA card...

Out of the 3 devices the Old vodafone was the only one that worked!

I went back to the E620 and decided just for sake of testing to try connect and it worked as-well. Seems with that card you NEED a sim card in device even if you just wan't it to pick up and hence why it didn't pick up!

Then Back to the E220...
Solved .... Seems that if you add a profile you MUST specify the card to use and not leave it as ANY because it won't display it as a available connection otherwise... Why i didn't have the option for the E220.... Well it seems sometimes the card was listed otherwise Greyed out as ANY when creating connection and i only created the connection once when it didn't display it!

Tested this few times...

Thanks anyways guys.... Im just glad i actually solved it before going on road!!!!

---

### Post by Paxy on 2011-06-24
Good day all,

I have a new type of a problem with combination Ubuntu 10.10 and Huawei E220.
Connection cuts every now and then. It has remained on for 24h and it has cut several times in one hour.

Sometimes disconnecting---> waiting 1min---> reconnecting helps, sometimes I must disconnect the stick, restart computer and reconnect the stick.

And yes, I have the additional power wire connected, so that is not the issue...

Now when it works, it works perfectly...

---

