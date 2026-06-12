---
title: "IP address is not being assigned - lots of helpful info included!"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by garethc on 2007-05-03
hi all,

i've tried to do some detective work on this one but my ubuntu knowledge is too poor for me to proceed any further. this is a continuation of an earlier thread that 'morphed' somewhat -- [http://ubuntuforums.org/showthread.php?p=2583437#post2583437](http://ubuntuforums.org/showthread.php?p=2583437#post2583437)

i can't interpret the feedback from the various commands I thought would provide useful output regarding my eth1 issues. i would be greatful if someone could help me out here -- muchos gracias!!

'sudo ifconfig' gives:

```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:07:10:B2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:08:54:E2:61:CC  
          inet6 addr: fe80::208:54ff:fee2:61cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5052 (4.9 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:07:10:B2  
          inet addr:169.254.5.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

eth1:avah Link encap:Ethernet  HWaddr 00:08:54:E2:61:CC  
          inet addr:169.254.8.215  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3796 (3.7 KiB)  TX bytes:3796 (3.7 KiB)

```

'sudo dhclient eth1' gives:

```
Listening on LPF/eth1/00:08:54:e2:61:cc
Sending on   LPF/eth1/00:08:54:e2:61:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

'sudo tcpdump -vvn -i eth1' gives:

```
tcpdump: WARNING: eth1: no IPv4 address assigned
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
12:59:51.004121 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
12:59:58.003907 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, secs 7, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:00:05.003950 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, secs 14, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:00:19.004014 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, secs 28, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:06:40.001962 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:06:43.001802 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, secs 3, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:06:51.001962 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, secs 11, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:07:01.001929 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, secs 21, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]

8 packets captured
8 packets received by filter
0 packets dropped by kernel

```

** note that i CTRL+C'd the tcpdump process after ab out 2 minutes because it seemed to be in a loop giving similar data over and over - was I wrong to cancel?!

---

### Post by garethc on 2007-05-03
the contents of /etc/network/interfaces --

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

