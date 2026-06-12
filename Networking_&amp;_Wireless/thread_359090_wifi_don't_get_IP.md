---
title: "wifi don't get IP"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by maurizio73 on 2007-02-11
Hi All
I'm using ubunt but I'm not able to connect it to my wifi network with wep security. Ip address is not assigned. I report the output of some commands run on my laptop.
Thanks Maurizio

iwconfig output is:
maurizio@maurizio:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"23maurizio73"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:37:40:31   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/94  Signal level=-45 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
====================

netstat -r command shows that wireless interface doesn't have IP assigned:

maurizio@maurizio:~$ netstat -r
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
default         192.168.1.3     0.0.0.0         UG        0 0          0 eth0

====================

I tried to anble dhcp client on the wireless interface (ath0) by the command:
sudo dhclient ath0

maurizio@maurizio:~$ sudo dhclient ath0
Password:
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:20:93:5e:a6
Sending on   LPF/ath0/00:0f:20:93:5e:a6
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

===================

the content  of /etc/networks/interfaces is:

maurizio@maurizio:/etc/network$ more interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


auto wlan0
iface wlan0 inet dhcp


iface ath0 inet dhcp
wireless-essid 23maurizio73
wireless-key A7AB090D1EDAD9F724E5578CF7

auto ath0

auto eth0
maurizio@maurizio:/etc/network$ 

===================

---

### Post by Floppyjoe on 2007-02-11
Possibly adding some lines in your /etc/network /interfaces file under your wireless interface might help like:
```
wireless-mode managed
wireless-channel 6
```
Where wireless-channel is set to the channel of your router.

---

