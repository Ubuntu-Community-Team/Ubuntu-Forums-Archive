---
title: "no ip address on wireless, wrong nameserver"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by blabla on 2006-09-26
Hi,

I've got a ralink wireless pcmcia card using the rt2500 driver. Has always logged me onto my modem come dhcp router a treat until I tried to crack into Geneva airport. Here is what I get now...

iwconfig:

[HTML]ra0       RT2500 Wireless  ESSID:"xxxxxxx"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm 
          RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:restricted
          Link Quality=0/100  Signal level=-60 dBm  Noise level:-218 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]ESSID and key are correct, but when I do dhclient ra0 I get:[HTML]Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:80:5a:35:1e:c4
Sending on   LPF/ra0/00:80:5a:35:1e:c4
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 10.34.30.1 port 67
binding to user-specified port 68
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:80:5a:35:1e:c4
Sending on   LPF/ra0/00:80:5a:35:1e:c4
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 192.168.178.1 port 67 interval 7
DHCPDISCOVER on ra0 to 192.168.178.1 port 67 interval 12
DHCPDISCOVER on ra0 to 192.168.178.1 port 67 interval 12
DHCPDISCOVER on ra0 to 192.168.178.1 port 67 interval 15
DHCPDISCOVER on ra0 to 192.168.178.1 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/HTML]The DHCPRELEASE line incl port 67 made me wary but dhclient -p 68 ra0 gives me the following:[HTML]binding to user-specified port 68
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:80:5a:35:1e:c4
Sending on   LPF/ra0/00:80:5a:35:1e:c4
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/HTML]My /etc/resolv.conf points at my router. I also tried turning off the encryption but still did not manage to get an IP address](*,) 

Also, here is my ifconfig:[HTML]ra0       Link encap:Ethernet  HWaddr 00:80:5A:35:1E:C4
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13803 errors:16 dropped:16 overruns:0 carrier:0
          collisions:71 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:514435 (502.3 KiB)
          Interrupt:11 Base address:0x8000[/HTML]And dmesg:[HTML][ 3409.158223] pccard: CardBus card inserted into slot 1
[ 3409.160140] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[ 3409.160172] rt2500 1.1.0 CVS 2005/07/10 http://rt2x00.serialmonkey.com
[ 3409.160486] PCI: Setting latency timer of device 0000:06:00.0 to 64
[ 3411.521108] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel[ 3411.521156] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  5  5  5  5  5  dBm Maximum[/HTML]What is preventing me from logging onto my network? Anybody any ideas out there :confused:

---

