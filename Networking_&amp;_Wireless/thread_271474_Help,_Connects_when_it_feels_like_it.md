---
title: "Help, Connects when it feels like it"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by Skuggi on 2006-10-04
Ok, I have a dell e1505 with the damned broadcom 1390 chipset.  After hell getting ndiswrapper to work, I finally got everything setup and was I happy.  Now the problem is, is going to connect to the networks, sometimes it connects sometimes it doesnt. This is happening on both encrypted and open networks, and over 3 different networks i use (home, work, school).  Home, i have wep, turned it on and off, got it to connect, havent been able to lately. 

I am using Wireless Assistant 0.5.5 which is showing the networks fine when I scan, but the connection keeps failing. 

Oh yea, I've tried both DHCP and manually entering in the addressing.  I seem to have better luck when I enter it manually and disable wep but it still has issues.

**the gods have tfavored me** I launched wireless assistant from the command line to check for errors.  It actually connected this time, but heres the code it says bad devices???

```
skuggi@skuggi-laptop:/usr/share/doc$ sudo wlassistant
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): wlan0
Permissions checked.
ifconfig_status: /sbin/ifconfig wlan0
scan: /sbin/iwlist wlan0 scan
KWrited - Listening on Device /dev/pts/2
Networks found: 2
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
Gateway address: 10.120.1.1
Checking for active connection.
kill_dhcp: /sbin/dhclient -r wlan0
==>stderr: Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:16:ce:5b:d3:6a
Sending on   LPF/wlan0/00:16:ce:5b:d3:6a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.10.1.177 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
ifup: /sbin/ifconfig wlan0 up
iwconfig_set: /sbin/iwconfig wlan0 mode managed channel 6 key open C725BADFF8 essid Streamline
==>stderr: Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.
iwconfig_ap: /sbin/iwconfig wlan0 ap 00:12:17:AE:34:E9
ifconfig_dhcp: /sbin/dhclient -q wlan0
Internet now accessible.

```

---

### Post by pixel_pixie on 2006-10-15
Hi, 
I've got the same problem as you. My laptop (Acer Aspire 1640Z) used to be able to connect vie Wireless Assistant 0.5.5 until a few days ago  when it stopped for no reason. Then I tried the WiFi Radar - same thing. Worked for a couple of days and no more. Now the WL Assistant gives me the same error message as you whereas the WiFi Radar claims it is connected to a network, even if I turn the card off.
Did you solve you problem and if yes - how?

oh, i forgot. i tried running it with the command line, it gets to "connection unreachable"

---

### Post by j0rg3 on 2006-10-15
I get the same error trying to compile HelloWorld in KDE C++ and something similar (if i recall correctly) when I tried to compile in GAMBAS.

My theory is that Ubuntu doesn't like Pittsburgh.

You should probably move.

---

### Post by j0rg3 on 2006-10-15
Did you find your answer?

If not I will look for the one I found.

I just needed to go into the config file for X and comment out some lines about a wacom tablet.

---

