---
title: "Cannot get an IP address."
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Jacob, The Lesser on 2007-12-04
Just installed Linux on an older computer. Everything works fine, minus the wireless card.
It is a Linksys WMP11, and I am using the bcm43xx firmware for it's broadcom chipset.
The card is recognized, has a driver, and can "see" the wireless networks in range (including my own) but cannot connect to them. When I attempt to manually connect to my network using the dhclient, but to no avail. The only problem I can see is that I am not receiving an IP address. My router's security is disabled, and the dhcp broadcasting is turned on.

More Info:

**ifconfig yields:**

eth1      Link encap:Ethernet  HWaddr 00:06:25:1B:CF:3A  

          inet6 addr: fe80::206:25ff:fe1b:cf3a/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:48 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4741 errors:0 dropped:1 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:18877 (18.4 KB)  TX bytes:210333 (205.4 KB)

          Interrupt:9 Base address:0xc000 

**iwconfig yields:**

eth1      IEEE 802.11b  ESSID:"Belkin_Pre_N"  Nickname:"Broadcom 4301"

          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   

          Bit Rate=1 Mb/s   Tx-Power=16 dBm   

          RTS thr: off   Fragment thr: off

          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**sudo dhclient eth1 Yields:**

There is already a pid file /var/run/dhclient.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth1/00:06:25:1b:cf:3a

Sending on   LPF/eth1/00:06:25:1b:cf:3a

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14

No DHCPOFFERS received.

No working leases in persistent database - sleeping.


Any help or ideas would be greatly appreciated. I've already gone through some of the documentation and troubleshooting guides I've found [http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29")

---

### Post by csat on 2007-12-04
> **Jacob, The Lesser said:**
> 

Any help or ideas would be greatly appreciated. I've already gone through some of the documentation and troubleshooting guides I've found [http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29")

Have you tried this also?

[http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys](http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys)

---

### Post by Jacob, The Lesser on 2007-12-04
Thanks, but I cannot find anything in that post that helps my problem. There is no security enabled at this point, so I cannot blame that.

---

