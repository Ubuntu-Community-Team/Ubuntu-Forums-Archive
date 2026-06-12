---
title: "MA-101 almost works"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by GarthK on 2007-02-03
I am ultimately trying to get my Belkin Pre-N Wireless card to work but all of the sites assume that you have an existing connection to download with. My old Dell Inspiron 3500 doesn't have an available connection but I do have an old Netgear MA-101 that I would like to use to bootstrap the Belkin. It almost works... I can get an IP address via DHCP from my server and no errors are reported but it won't ping nor can it be seen. I've followed several sites to diagnose but nothing works. I've included several lists of various commands to show that status.

Any help greatly appreciated!

Thanx,
Garth

<interfaces>

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid Belkin_Pre-N_454856
wireless-key <string of 16 hex characters>

<ifconfig>

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2440 (2.3 KiB)  TX bytes:2440 (2.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:3B:AA:4F  
          inet addr:10.20.40.61  Bcast:10.20.40.255  Mask:255.255.255.0
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5555 (5.4 KiB)  TX bytes:4518 (4.4 KiB)

<iwconfig>

lo        no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"Belkin_Pre-N_454856"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:28:85:42   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=0/0  Signal level=120/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

<iwlist rate>

lo        no bit-rate information.

wlan0     4 available bit-rates :
	  1 Mb/s
	  2 Mb/s
	  5.5 Mb/s
	  11 Mb/s
          Current Bit Rate:11 Mb/s

<lsusb>

Bus 002 Device 003: ID 0864:4102 NetGear, Inc. MA101 802.11b Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05af:0408 Jing-Mold Enterprise Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

<route>

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.20.40.0      *               255.255.255.0   U     0      0        0 wlan0
default         10.20.40.1      0.0.0.0         UG    0      0        0 wlan0


<networking restart>

 * Reconfiguring network interfaces...       [80G There is already a pid file /var/run/dhclient.wlan0.pid with pid 4426
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:09:5b:3b:aa:4f
Sending on   LPF/wlan0/00:09:5b:3b:aa:4f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.20.40.4 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:09:5b:3b:aa:4f
Sending on   LPF/wlan0/00:09:5b:3b:aa:4f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPOFFER from 10.20.40.4
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.20.40.4
bound to 10.20.40.61 -- renewal in 41900 seconds.

---

### Post by GarthK on 2007-02-05
As a follow-up, if anyone can point me to an Edgy-approved, 10/100 USB NIC that works out-of-the-box, I'd appreciate that as well. It never hurts to have one of them available in a pinch.

Thanx,
Garth

---

### Post by GarthK on 2007-02-10
To answer my own question, the Belkin F5D5050 USB 10/100 Ethernet Adapter, Version 2101, works out-of-the box, at least for Xubuntu 6.10.

Just FYI...

---

### Post by ChiJoan on 2008-06-23
Hello,

Thanks for letting me know about my Belkin USB NIC.  Puppy Linux didn't see it, I'll try Xubuntu, but I don't know if my Compaq Prosignia 162 P2 at 366 MHz with about 190 MEG RAM is powerful enough for it.

Good luck on your newer hardware,
ChiJoan in Reno,NV

---

