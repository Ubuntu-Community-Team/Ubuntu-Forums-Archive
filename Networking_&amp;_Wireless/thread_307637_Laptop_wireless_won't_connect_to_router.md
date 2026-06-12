---
title: "Laptop wireless won't connect to router?"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by fisherman783 on 2006-11-26
I've installed Xubuntu 6.06 on a Dell Latitude laptop for my parents that was known to work under XP without problem.  Since the Linux switch, I haven't been able to get it to connect wirelessly to their 2wire router.  I can get the computer to get internet by using an ethernet connection to the router, but it needs to be able to use wireless.  The problem appears to be that the laptop can't acquire an IP address, but I get the feeling the real problem might be more fundamental.  I have little experience with wireless problems in general, and none in Linux.

With no internet out of the box, I opened up the network manager (network-admin) to try and configure things:
```
Wireless connection
The interface eth1 is not active

Ethernet connection
The interface eth0 is active

Modem connection
The interface ppp0 is not configured
```
I opened the properties dialog for the wireless device, entered the SSID and WEP key.  Then I clicked the button to activate the device and a dialog came up for about a minute:
```
Activating interface "eth1"
```
When the dialog disappears, the connection list now reads:
```
The interface eth1 is active
```
I click the OK button and the window is busy for another minute or so.  Still no internet, though.  So I open the network manager again and in the connection list, I see:
```
The interface eth1 is not active
```
I have looked up wireless guides and tutorials, and haven't found anything that helps.  One user suggested deactivating the ethernet connection, which didn't help.

As far as other simlar problems people have posted about, I have tried several things from the command line, with output that doesn't quite match up with any other problems I could find out there:
```
user@comp:~$ sudo ifdown eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:02:2d:57:8f:4b
Sending on   LPF/eth1/00:02:2d:57:8f:4b
Sending on   Socket/fallback
user@comp:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Connection timed out
SIOCSIFFLAGS: Connection timed out
Listening on LPF/eth1/00:02:2d:57:8f:4b
Sending on   LPF/eth1/00:02:2d:57:8f:4b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
(and so on)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

An lspci command doesn't seem to list a wireless device:
```
user@comp:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420
0000:02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
```

The wireless connection is also not listed with ifconfig: (this is the output when the ethernet connection is active; when it is inactive, only the local loopback entry appears)
```
user@comp:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E5:69:7B
          inet addr:192.168.1.64  Bcast: 192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fee5:697b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:42734622 (40.7 MiB)  TX bytes:1651604 (1.5 MiB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20200 (19.7 KiB)  TX bytes:20200 ( 19.7 KiB)
```

But iwconfig does display some info:
```
user@comp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"2wire193"  Nickname:"2wire193"
          Mode:Managed  Bit Rate:11 Mb/s
          RTS thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sit0      no wireless extensions.
```

I believe the wireless device is using the orinoco drivers, which might make this relevant:
```
user@comp:~$ sudo lsmod
Module                 Size   Used by
...
orinoco_cs             17928  1
orinoco                43156  1 orinoco_cs
hermes                  7808  2 orinoco_cs,orinoco
...
```

Trying to use iwlist to scan for the router:
```
user@comp:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.
```

I've tried using wifi-rader to connect, which gives me the same output as the iwlist scan, as well as the DHCPDISCOVER error from above.  

Any help or suggestions would be greatly appreciated.

---

### Post by wmatlock on 2006-11-26
Fisherman783,

Go to the following link and see if you can find more detailed instructions on your particular card. I think that orinoco is supported from a basic install because I have seen that name while trying to install my linksys card.

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Good Luck

---

