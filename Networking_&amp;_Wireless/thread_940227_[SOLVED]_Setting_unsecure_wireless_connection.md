---
title: "[SOLVED] Setting unsecure wireless connection"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by Bobrm2 on 2008-10-06
I have Hardy installed; but having difficulty reinstalling my wireless network. The following is what I've done so far. would someone pick over this and tell me what I need to do? Thanks

bob@bob-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MSHOME"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:55:54:7F   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-54 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bob@bob-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:e9:b7:f9:17  
          inet6 addr: fe80::215:e9ff:feb7:f917/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:9859 (9.6 KB)

ath0:avahi Link encap:Ethernet  HWaddr 00:15:e9:b7:f9:17  
          inet addr:169.254.8.100  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:19:21:ba:78:55  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:feba:7855/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1465135 (1.3 MB)  TX bytes:197551 (192.9 KB)
          Interrupt:21 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54300 (53.0 KB)  TX bytes:54300 (53.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-B7-F9-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14513 errors:0 dropped:0 overruns:0 frame:282
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1469515 (1.4 MB)  TX bytes:17811 (17.3 KB)
          Interrupt:22 

bob@bob-desktop:~$ sudo ifconfig ath0 down
[sudo] password for bob: 
bob@bob-desktop:~$ dhclient -r ath0
There is already a pid file /var/run/dhclient.pid with pid 6601
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
bob@bob-desktop:~$ sudo ifconfig ath0 up
bob@bob-desktop:~$ sudo iwconfig ath0 "MSHOME"
iwconfig: unknown command "MSHOME"
bob@bob-desktop:~$ sudo iwconfig ath0"MSHOME"
ath0MSHOME  No such device

bob@bob-desktop:~$ sudo iwconfig ath0 essid "MSHOME"
bob@bob-desktop:~$ iwconfig ath0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Operation not permitted.
bob@bob-desktop:~$ help iwconfig
-bash: help: no help topics match `iwconfig'.  Try `help help' or `man -k iwconfig' or `info iwconfig'.
bob@bob-desktop:~$ man -k iwconfig
iwconfig (8)         - configure a wireless network interface
bob@bob-desktop:~$ iwconfig ath0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Operation not permitted.
bob@bob-desktop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 6601
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:b7:f9:17
Sending on   LPF/ath0/00:15:e9:b7:f9:17
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bob@bob-desktop:~$ sudo iwconfig ath0 mode Managed
sudo: unable to resolve host bob-desktop
bob@bob-desktop:~$ 

One thing I haven't done is to reconfigure the setting on the hardwired XP pro box. Thanks

Bob:confused:

---

### Post by lswb on 2008-10-06
The iwconfig and dhclient commands need to be run with sudo (or as root) when you are changing any settings. Try something like this:

sudo ifconfig ath0 down
sudo iwconfig ath0 mode managed essid "MSHOME"
sudo ifconfig ath0 up
sudo dhclient ath0

Also for atheros you may want the madwifi-tools package.

---

### Post by Bobrm2 on 2008-10-07
Thanks you for your quick reply, below are the result, and now download madwifi. Correct me if I am wrong; it seems that I am "turning" off ifconfig, indicating that "MSHOME" is the new essid (ssid in this case), and turning ifconfig back on, finally checking to see results. If this is incorrect then where can I locate what I told Linux to do? Thanks once more.
Bob

bob@bob-desktop:~$ sudo ifconfig ath0 down
[sudo] password for bob: 
bob@bob-desktop:~$ sudo iwconfig ath0 mode managed essid "MSHOME"
bob@bob-desktop:~$ sudo ifconfig ath0 up
bob@bob-desktop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:b7:f9:17
Sending on   LPF/ath0/00:15:e9:b7:f9:17
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bob@bob-desktop:~$

---

### Post by Bobrm2 on 2008-11-03
Ran into the "Wicd" program; in my searches to connect wirelessly. Wicd is a little slow sometimes, but then sometimes it connects almost immediately upon startup. Thanks you for the assist.

Bob

---

