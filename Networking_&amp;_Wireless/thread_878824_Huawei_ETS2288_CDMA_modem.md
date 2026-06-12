---
title: "Huawei ETS2288 CDMA modem"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by tilugulilwa on 2008-08-03
Hello forum members,

I am struggling to have my Huawei ETS2288 CDMA modem working on Ubuntu (kernel version  2.6.24-16-generic.

There are several proposed solutions but i think with Ubuntu 8.04 it is not working.

Please assist me.

Regards,

Frank Tilugulilwa ( Tanzania)

---

### Post by peterroots on 2008-08-06
Since upgrading to Kubuntu8.04 I have lost the ability to use wvdial to connect to the internet with a CDMA phone.  As this phone is widely used in Tanzania, and (I think) other parts of East Africa this is a major problem for me and potentially a lot of others.
This used to work via a fix at [http://ubuntuforums.org/showthread.php?t=258709&highlight=Huawei+ETS2288](http://ubuntuforums.org/showthread.php?t=258709&highlight=Huawei+ETS2288) but not any more!!

Wvdial reports it is unable to open /dev/ttyUSB0: not such file or directory
I have also tried using ppp to dial out with network manager and my system log shows

05/08/08 17:19:46	Peter	NetworkManager	<debug> [1217956786.527142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3410_TUSB3410'). 

05/08/08 17:19:46	Peter	NetworkManager	<debug> [1217956786.822488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3410_TUSB3410_if0'). 

05/08/08 17:20:01	Peter	NetworkManager	<info>  Activating dialup device ttcl via Modem (ppp1) ... 

05/08/08 17:20:02	Peter	NetworkManager	<WARN>  nm_system_activate_dialup(): Couldn't activate dialup device ttcl via Modem (ppp1) - 134894896 

05/08/08 17:20:02	Peter	pppd[6780]	In file /etc/ppp/peers/ttcl: unrecognized option '/dev/ttyUSB0'

If any anyone can shed any light on this I would be very grateful


I have a file called 026_ti_usb_3410.rules that I added according to help I found for ubuntu7.10 or earlier (may have gone back to 6.04, I can't remember but it has worked fine on serveral versions of Kubuntu upto and inculding 7.10)
This file contains the following

#TI USB 3410
 SUBSYSTEM=="usb_device" ACTION=="add", SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410"
 SYSFS{bNumConfigurations}=="2",
 SYSFS{bConfigurationValue}=="1",
 RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"

and is in my /etc/udev/rules.d/ folder

output from the last part of dmesg after plugging in the 
Huawei ETS2288 CDMA phone

[  368.691674] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  368.885763] usb 2-2: configuration #1 chosen from 1 choice
[  147.704174] usbcore: registered new interface driver usbserial
[  147.704581] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  147.704826] usbcore: registered new interface driver usbserial_generic
[  147.704830] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  369.361002] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 3410 1 port adapter
[  369.361049] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 5052 2 port adapter
[  369.361105] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[  369.361124] usbcore: registered new interface driver ti_usb_3410_5052
[  369.361131] /build/buildd/linux-2.6.24/drivers/usb/serial/ti_usb_3410_5052.c: TI USB 3410/5052 Serial Driver v0.9

Any help gratefully received

I have since discovered that the udev rules file I used to use now appears to be irrelevant as I get the modem showing up is lsusb and the same (more or less) messages in dmesg and the system log as I do with the rules file.
Any Idea on how to fix the error -5 on the probe would be most helpful.
Thanks

---

### Post by peterroots on 2008-08-15
As nobody seems to have any good ideas on this and I am stumped I have reported it as a bug
[https://bugs.launchpad.net/ubuntu/+bug/258093](https://bugs.launchpad.net/ubuntu/+bug/258093)
I hope that this leads to a stable solution to this problem for TTCL users in Tanzania.

---

### Post by madra on 2008-08-18
Hi,iam Madra from Uganda...i have a Huawei ETS2056 provided by UTL,i installed Ubuntu 8.04 LTS
and i tried using the modem but poof anyways i got it to read the modem as ttyUSB0 by entering 
modprobe usbserial vendor=0x451 product=0x3410 in the terminal before plugging in the cable...
iam stuck right there cos it still doesnt seem to dial,anways if you do get it to dial,let me know...
[email]madradavid@yahoo.com[/email]

---

