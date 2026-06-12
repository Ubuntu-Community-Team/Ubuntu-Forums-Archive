---
title: "[SOLVED] Wireless connection broken by Hardy upgrade"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by wwastro on 2008-07-22
I had a working Gutsy installation on a Dell 6400 Inspiron laptop, normally connecting to the internet by wireless (yes, I used kevdog's guide for manual installation from here:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) )

Having upgraded to Hardy, the wireless connection is now broken.

With the present setup, the response to _sudo ishw -C network_ (before making the current ethernet connection via interface eth0) was:

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:94:65:62
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:bd:3e:2f
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no module=ssb multicast=yes port=twisted pair

It appears from this that wmaster0 has now replaced eth1 as the wireless interface (yet I understand that wmaster0 cannot be used directly by me in setting up a wireless connection). The response to _ifconfig_ is currently:

eth0      Link encap:Ethernet  HWaddr 00:15:c5:bd:3e:2f
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3989714 (3.8 MB)  TX bytes:375607 (366.8 KB)
          Interrupt:22

eth1      Link encap:Ethernet  HWaddr 00:18:de:94:65:62
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:720 (720.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:18:de:94:65:62
          inet addr:169.254.7.15  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4140 (4.0 KB)  TX bytes:4140 (4.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-94-65-62-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and the response to _iwconfig_ is:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:D3:B3:6E
          Bit Rate=54 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality=100/100  Signal level=-17 dBm  Noise level=-50 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The response to an attempt to connect by wireless using kevdog's instructions (via a shell script - no mention of wmaster0 in the script, by the way) is:

There is already a pid file /var/run/dhclient.pid with pid 6961
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:18:de:94:65:62
Sending on   LPF/eth1/00:18:de:94:65:62
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:18:de:94:65:62
Sending on   LPF/eth1/00:18:de:94:65:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any helpful suggestions welcomed - there may be a fix or workaraound, but I have yet to find one!

Thanks in advance.:confused::confused:

---

### Post by wwastro on 2008-08-01
Please note, this problem is now solved thanks to kevdog and chili555. My /etc/network/interfaces file contained conflicts, now resolved.

---

### Post by barkingcorndog on 2008-08-11
This thread is pretty much worthless without showing how the problem was solved.

---

