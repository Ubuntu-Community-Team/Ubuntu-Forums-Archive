---
title: "Wireless DHCP problem with intel2200bg card"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by kilou on 2006-12-12
Hi,

I'm running Ubuntu 6.10 and after numerous trials my wireless is still not working. I have an Intel 2200 BG wireless card and this card is supposed to work "out of the box" with Edgy.

I have installed GNOME network manager and can connect to my wireless network but I can't browse the internet and I cannot ping adresses (either IP or names). I can access my wireless router configuration (through wireless connection) and I removed the WEP encryption. But again I can connect to the network but cannot browse or ping anything. My wired connection works fine with DHCP but my wireless is still not working. I tried to put a static IP address but I'm still not able to browse or ping anything! I also compiled and installed the latest kernel 2.6.19 and the latest IPW2200 firmware version 3 but still have the exact same issues. Disabling the wired connection and leaving only the wireless connection enabled in System/administration/Networking doesn't bring anything as well

I really don't understand what's happening. My card is nothing fancy and I know people get it working in Ubuntu 6.10 but what am I doing wrong here??

My wireless connection is eth1. Wired connection works perfectly with DHCP. I can also access my router (DLink DI-624) configuration through wireless. Any help greatly appreciated!

Output of some commands:

**iwconfig**
lo no wireless extensions.

eth1 IEEE 802.11g ESSID:"Kilou"
Mode:Managed Frequency:2.437 GHz Access Point: 00:13:46:A7:AE:50
Bit Rate:54 Mb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=93/100 Signal level=-35 dBm Noise level=-88 dBm
Rx invalid nwid:0 Rx invalid crypt:256 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0 no wireless extensions.

**lspci**
01:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

**ping -c 4 [www.google.com](www.google.com)**
ping: unknown host [www.google.com](www.google.com)
[B]
ping -c 4 216.239.39.99[/B]
PING 216.239.39.99 (216.239.39.99) 56(84) bytes of data.

--- 216.239.39.99 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

**sudo gedit /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid kilou
wireless-key **********

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

**sudo iwlist eth1 scan**
eth1 Scan completed :
Cell 01 - Address: 00:13:46:A7:AE:50
ESSID:"Kilou"
Protocol:IEEE 802.11bg
Mode:Master
Channel:6
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality=92/100 Signal level=-53 dBm
Extra: Last beacon: 104ms ago

**sudo dhclient eth1**
There is already a pid file /var/run/dhclient.pid with pid 11994
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:14:84:86
Sending on   LPF/eth1/00:12:f0:14:84:86
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 254513 seconds.


PS: my laptop is an MSI S260 (centrino)

---

### Post by inetd on 2006-12-12
please print output from

netstat -r

---

### Post by kilou on 2006-12-12
Thanks for your help! The output of **netstat -r** is as follow:

Connected to wireless network (eth1):

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth1
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth1

Connected to wired network (eth0):

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.112.0   *               255.255.255.0   U         0 0          0 eth0
default         192.168.112.1   0.0.0.0         UG        0 0          0 eth0

---

### Post by kilou on 2006-12-12
Any idea?

---

