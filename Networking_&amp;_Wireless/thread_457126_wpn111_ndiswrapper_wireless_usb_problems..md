---
title: "wpn111 ndiswrapper wireless usb problems."
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by charliemcf on 2007-05-28
hello im new here so not much good at linux.
i have tried various other posts opn the issue before nyone asks and they havn't seemes to work.

SPECS: Dell E521, 2Gig Ram, Feisty/ Vista Dual boot, Amd64 x2 4200+, Ati X1300 pro.

I have the drivers copied from the "C:\Windows\System32\Driverstore" Directory of vista and have succesfully installed trhem with ndiswrapper.

when i do ```
sudo ndiswrapper -l
```

I get:

```
* : driver installed
        device (1385:5F01) present
netwpn11 : driver installed
        device (1385:5F01) present
```

If i do ```
charlie@dell:~$ sudo ifup wlan0

```

I get:

```
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

i have added ndiswrapper to the end of the file as stated using gedit, and i have configured my essid settings etc.

the wireless still does not start flashing or show in the "network" selection, even after "sudo depmod -a" and "sudo modprobe ndiswrapper" "sudo ndiswrapper -m" with several reboots, open windows then ubuntu and vice versa. i am using the wpn111 as i type in vista with no problems.;)




any thoughts are appreciated.

//charlie//

---

