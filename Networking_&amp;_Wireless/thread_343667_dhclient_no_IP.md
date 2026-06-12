---
title: "dhclient no IP"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by ububuL on 2007-01-21
I am not able to connect to any networks except the one I listed in the /etc/network/interfaces. 
When I try to connect to a non-secure network by using the following commands, I receive no IP. I also try it with wifi-radar and still no IP.
```
sudo iwconfig eth1 essid "openednetwork"
```
```
sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:f9:fe:36
Sending on   LPF/eth1/00:90:4b:f9:fe:36
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
Trying recorded lease 192.168.0.4
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

```
No working leases in persistent database - sleeping.

==================================================
However, when I connect to the network I listed in the /etc/network/interfaces using ifup, things work pretty well.
```
sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:f9:fe:36
Sending on   LPF/eth1/00:90:4b:f9:fe:36
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.4 -- renewal in 98834 seconds.

```
output of /etc/network/interfaces.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp
wireless-essid ZZZZ
wireless-key x24x


auto ath0
iface ath0 inet dhcp

```
I hope somebody has a solution or see a solution somewhere in the forum. Thanks for reading.

---

### Post by phossal on 2007-01-21
Did you try removing the specific configuration from /etc/net*/interfaces?

---

### Post by ububuL on 2007-01-22
> **phossal said:**
> Did you try removing the specific configuration from /etc/net*/interfaces?

I did but it did not help. The thing I found strange was that when I ran
```
sudo iwconfig
```
after 
```
sudo iwconfig eth1 essid "openednetwork"
```
the output is
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  Nickname:"openednetwork"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```
The ESSID never got set? Don't understand. :confused:

---

### Post by phossal on 2007-01-22
Try:

```
sudo iwconfig eth0 essid OPENEDNETWORK channel <YOUR CHANNEL> nick ""
```
Eliminate the nick by setting the value "", use a channel, and make sure the case of your ESSID matches that of the router. In addition, make sure WEP/WPA is off, so no key parameter is needed.

---

### Post by ububuL on 2007-01-23
> **phossal said:**
> Try:

```
sudo iwconfig eth0 essid OPENEDNETWORK channel <YOUR CHANNEL> nick ""
```
Eliminate the nick by setting the value "", use a channel, and make sure the case of your ESSID matches that of the router. In addition, make sure WEP/WPA is off, so no key parameter is needed.

It is the same. I had to remove wifi-radar and /etc/network/interfaces so that when ubuntu boots and it connected to the open network. Then I ran, dhclient eth1 and valid IP would be obtained. This is really strange.

---

