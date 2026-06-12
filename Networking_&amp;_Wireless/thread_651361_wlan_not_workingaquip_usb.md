---
title: "wlan not working/aquip usb"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by nautu2000 on 2007-12-27
Hi,

I am trying to get my wlan working since 3 days but it still does not work. There is a lot of information available on the web but so far I could not figure out how to get it work. Actually, in the meanwhile I am quite confused :confused:

I have a usb adapter from a-quip, a/WLAN-1 I want to use with my linux (details betow).

I hope someone can help me with this :)


Ok, I am using the following system:

uname -a
Linux thq 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:4A:A0:01:B3
                    ESSID:"MCMC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


I am trying to use WPA2 (I know that the signal is working because I can check with my Mac that the wirless signal is present).



It seems to me that I can not get an IP address:

sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5544
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/06:50:43:00:21:d4
Sending on   LPF/wlan0/06:50:43:00:21:d4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



etc/network/interfaces looks like;

auto lo
iface lo inet loopback


After reading a lot of posting I deleted everything below the second line because of
[http://mylinux.suzansworld.com/?p=175](http://mylinux.suzansworld.com/?p=175)


In my opinion the network is recognized (MCMC) and the wlan adapter as well. But I can not get the IP. 

Does anyone have an idea. Pleaseeee :)

Thanks!

---

### Post by nautu2000 on 2007-12-28
I think the problem is that 'iwconfig' shows

essid:off/any
access point: not-associated

But I am not able to change this. This command
sudo iwconfig eth1 essid YourNetworkName key s:YourKey channel auto mode Managed
as described here
[https://answers.launchpad.net/ubuntu/+question/15423](https://answers.launchpad.net/ubuntu/+question/15423)
does not change it.

Any ideas?

---

