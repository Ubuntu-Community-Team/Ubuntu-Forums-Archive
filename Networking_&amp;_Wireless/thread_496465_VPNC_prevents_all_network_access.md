---
title: "VPNC prevents all network access"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by gabe_rosser on 2007-07-09
I used to use VPNC on Ubuntu 6.10 to allow me to access my university network, and it worked fine using the network-manager plugin.  However it seems to be broken in Ubuntu 7.04.  I import the settings from a .pcf file as standard and vpnc suggests that it has successfully connected (ifconfig reveals the created 'tun' device with a new IP address):

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:A0:07:BA
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2569606 (2.4 MiB)  TX bytes:279973 (273.4 KiB)
          Interrupt:16 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6376 (6.2 KiB)  TX bytes:6376 (6.2 KiB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
-00
          inet addr:129.67.117.71  P-t-P:129.67.117.71  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1390  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

However I can't access anything on the internet following this.  It works fine again after I break the VPN connection.

This problem occurs whether using vpnc directly or the plugin.

Any help would be hugely appreciated.

Thanks.

---

