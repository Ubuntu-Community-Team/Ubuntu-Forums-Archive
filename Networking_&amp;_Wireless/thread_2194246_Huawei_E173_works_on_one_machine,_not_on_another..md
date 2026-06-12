---
title: "Huawei E173 works on one machine, not on another."
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by adk on 2013-12-16
Hi,
My problem is very strange. I have two laptops running the same system (Kubuntu 13.10, x86_64, both up to date). I tried to use my USB dongle Huawei E173u-2 on both of them.

First system (running on EEE PC 1215N) detects and switches modem mode correctly, lsusb says:
```
ID 12d1:1436 Huawei Technologies Co., Ltd. E173 3G Modem (modem-mode)
```
and I'm able to use it in Network Manager.

When I tried to use exactly the same dongle on second laptop running exactly the same system but on different hardware (Asus K56C) it does not work at all. Lsusb shows:
```
Bus 003 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem)
```

Of course, I tried to switch it manually:
```
usb_modeswitch -v 0x12d1 -p 0x1446 -V 0x12d1 -P 0x1436 -M "55534243123456780000000000000011062000000100000000000000000000"
```

This does not help at all. Command output is:
```
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 003 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------

Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
Resetting message endpoint 0x01
-> Run lsusb to note any changes. Bye.
```

After that, device is still 1446.
Automatic usb_modeswitch also fails, here is the log:

```
USB_ModeSwitch log from Sun Dec 15 21:59:36 2013

Using global config file: /etc/usb_modeswitch.conf

Raw args from udev: /3-1:1.0

Bus ID for device not given by udev.
 Trying to determine it from kernel name (3-1:1.0) ...
Using top device dir /sys/bus/usb/devices/3-1

USB dir exists: /sys/bus/usb/devices/3-1
Warning: USB attribute "serial" not readable.

SCSI dir exists: /sys/bus/usb/devices/3-1
Warning: SCSI attribute "vendor" not readable.
Warning: SCSI attribute "model" not readable.
Warning: SCSI attribute "rev" not readable.
----------------
USB values from sysfs:
  idVendor	12d1
  idProduct	1446
  manufacturer	HUAWEI Technology
  product	HUAWEI Mobile
  serial	(null)
  bNumConfigurations	1
----------------
bNumConfigurations is 1 - don't check for active configuration
Found packed config collection /usr/share/usb_modeswitch/configPack.tar.gz
Searching entries named: /usr/share/usb_modeswitch/12d1:1446*
Searching overriding entries named: /etc/usb_modeswitch.d/12d1:1446*
SCSI attributes not needed, moving on.

Extracting config 12d1:1446 from collection /usr/share/usb_modeswitch/configPack.tar.gz
config: TargetVendor set to 12d1
config: TargetProduct set to 1001,1406,140b,140c,1412,141b,1432,1433,1436,14ac,1506,1511
Driver module is "option", ID path is /sys/bus/usb-serial/drivers/option1
! matched, now switching
Command to be run:
/usr/sbin/usb_modeswitch -I -W -D -s 20 -c /run/usb_modeswitch/current_cfg -u -1   -v 12d1 -p 1446 2>&1

Verbose debug output of usb_modeswitch and libusb follows
(Note that some USB errors are expected in the process)
--------------------------------

Reading config file: /run/usb_modeswitch/current_cfg

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.2.3 (C) Josua Dietze 2012
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1446
TargetVendor=   0x12d1
TargetProduct=  not set
TargetClass=    not set
TargetProductList="1001,1406,140b,140c,1412,141b,1432,1433,1436,14ac,1506,1511"

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
QisdaMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
NeedResponse=0
ResponseEndpoint= not set

InquireDevice disabled
Success check enabled, max. wait time 20 seconds
System integration mode enabled


Looking for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 No devices in target mode or class found
Looking for default devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Found device in default mode, class or configuration (1)
Accessing device 009 on bus 003 ...
Skipping the check for the current configuration
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
Resetting message endpoint 0x01

Checking for mode switch (max. 20 times, once per second) ...
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0003
  searching devices, found USB ID 12d1:1446
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 13d3:5165
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 No new devices in target mode or class found

Mode switch has failed. Bye.

fail:
--------------------------------
(end of usb_modeswitch output)

USB dir exists: /sys/bus/usb/devices/3-1
Warning: USB attribute "serial" not readable.

All done, exiting
```

I also tried many tricks found in the internet, like loading usbserial with specified vendor, but this does not help. Comparing usb_modeswitch log with log from the working computer it seems, that USB device is not restarted after mode switching - see the fragment from working modeswitch session:
```

Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
 Could not reset endpoint (probably harmless): -71
Resetting message endpoint 0x01
 Could not reset endpoint (probably harmless): -19
 Device is gone, skipping any further commands

```

The fragment "device is gone" is missing on second computer. Seems like reset fails.
Any ideas?

---

### Post by adk on 2013-12-19
I made a progress with this issue. The manual command works, when I add the -I switch, i.e.:
```
usb_modeswitch -I -v 0x12d1 -p 0x1446 -V 0x12d1 -P 0x1436 -M "55534243123456780000000000000011062000000100000000000000000000"
```
Now, modem is changed to 12d1:1436, disconnects from the BTS (must wait a moment to find signal again), but after that it works.

Now I tried to make this work automagically, but without success. I extracted file 12d1:1446 from /usr/share/usb_modeswitch/configPack.tar.gz to /etc/usb.modeswitch.d. The message inside this file is identical to this used by me manually. According to the /var/log/usb_modeswitch.log, script now tries to execute the following command after device connected:
```
/usr/sbin/usb_modeswitch -I -W -D -s 20 -c /etc/usb_modeswitch.d/12d1:1446 -u -1   -v 12d1 -p 1446 2>&1
```

however the execution fails.

I disabled the automatic switch (in /etc/usb_modeswitch.conf) and then, after device connected, pasted the above command manually into root command line. For my surprise, it works. So, for some strange reason this command fails when executed automatically from usb_modeswitch udev hook, but works like a charm when launched manually from root cmdline. 
I tried to write a delay into /lib/udev/usb_modeswitch - I thought there was a time needed for the device to settle before switching - but this was a bad idea and does not help. Of course I tried to reinstall packages from usb_modeswitch (maybe something messed up with file rights?) - but still no success.

Do you have any ideas where to look for a bug?

---

### Post by Michele S on 2014-01-27
> **adk said:**
> I made a progress with this issue. The manual command works, when I add the -I switch, i.e.:
```
usb_modeswitch -I -v 0x12d1 -p 0x1446 -V 0x12d1 -P 0x1436 -M "55534243123456780000000000000011062000000100000000000000000000"
```
Now, modem is changed to 12d1:1436, disconnects from the BTS (must wait a moment to find signal again), but after that it works.

Now I tried to make this work automagically, but without success. I extracted file 12d1:1446 from /usr/share/usb_modeswitch/configPack.tar.gz to /etc/usb.modeswitch.d. The message inside this file is identical to this used by me manually. According to the /var/log/usb_modeswitch.log, script now tries to execute the following command after device connected:
```
/usr/sbin/usb_modeswitch -I -W -D -s 20 -c /etc/usb_modeswitch.d/12d1:1446 -u -1   -v 12d1 -p 1446 2>&1
```

however the execution fails.

I disabled the automatic switch (in /etc/usb_modeswitch.conf) and then, after device connected, pasted the above command manually into root command line. For my surprise, it works. So, for some strange reason this command fails when executed automatically from usb_modeswitch udev hook, but works like a charm when launched manually from root cmdline. 
I tried to write a delay into /lib/udev/usb_modeswitch - I thought there was a time needed for the device to settle before switching - but this was a bad idea and does not help. Of course I tried to reinstall packages from usb_modeswitch (maybe something messed up with file rights?) - but still no success.

Do you have any ideas where to look for a bug?

I'm sorry, but i have any idea, btw i want to thank you because your manual command helped me with my internet key, i made a script with the command and inserted script path in the udev rules instead of the default command launched for the plugging event of the device 12d1:1446

---

### Post by nadrach on 2014-05-16
Take a look at this thread from August 2013 (penultimate message):
 [http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173](http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173)

To paraphrase ... usb_modeswitch is making the wrong product ID change ...
> The problem is that usb_modeswitch switches the device from its default operation (product id 1446 which is a storage device) to the incorrect product id of 1436. In fact, it should change it to product id 140c, which is the correct product id for the modem.

The post then describes a file edit to change the configuration message sent by usb_modeswitch ... unfortunately none of the configuration files that the post specifies for 12.04 are present in 14.04.

---

