---
title: "rt73 problem (DWL-111)"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by hansson_14 on 2008-02-06
Hi!
I have this weird problem:
I try to use a wireless usb stick from D-Link, DWL-111. Ubuntu 7.10 doesn't find it, for example RutilT says: "Can't find any wireless network interface".
But i get the following using lsusb:

Bus 005 Device 002: ID 07d1:3c06 D-Link System 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0583:a00b Padix Co., Ltd (Rockfire) 
Bus 002 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000

dmesg says about usb bus 005:
[   34.423862] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   34.592061] usb 5-1: too many configurations: 60, using maximum allowed: 8

and:

[   35.011832] usb 5-1: configuration #1 chosen from 8 choices

I have blacklisted rt73 but then changed to blacklist rt73usb according to a tip in this forum. And I have manually added wlan0, rausb0 etc in /etc/network/interfaces.

My ifconfig -a shows:

eth0      Link encap:Ethernet  HWaddr 00:1A:92:04:37:2A  
          inet addr:78.82.229.94  Bcast:78.82.231.255  Mask:255.255.248.0
          inet6 addr: fe80::21a:92ff:fe04:372a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2453 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2310406 (2.2 MB)  TX bytes:446621 (436.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88 (88.0 b)  TX bytes:88 (88.0 b)

and ifconfig wlan0 up OR rausb0 up shows:

wlan0: ERROR while getting interface flags: Enheten finns inte=Device doesn't exist


Where do I start?

/Fredrik

---

### Post by xc3RnbFO8P on 2008-02-09
Have you check this HOWTO:

> [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by muxecoid on 2008-02-14
Any binaries for it?

---

