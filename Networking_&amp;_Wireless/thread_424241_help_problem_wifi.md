---
title: "help problem wifi"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by hgltqgs on 2007-04-26
hi all

iwconfig
> lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"3Com"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:45:00:f1   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-31 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

iwconfig

> lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"3Com"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:7C:BE:42:FE   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-31 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

route -n
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by sdide on 2007-04-26
I don't know that graphical manager.
but what does 

~# ifconfig -a

output?

---

### Post by hgltqgs on 2007-04-26
ifconfig -a
> 
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:C4:B0:D9  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fec4:b0d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:76960 errors:1 dropped:1 overruns:0 frame:0
          TX packets:77457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78607235 (74.9 MiB)  TX bytes:10772967 (10.2 MiB)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:D3:FC:10  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:6 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x4000 Memory:b010b000-b010bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496 (4.3 KiB)  TX bytes:4496 (4.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



---

### Post by sdide on 2007-04-26
you have no default gateway for eth1
do 
~# ip r a default via 192.168.1.1 dev eth1

if its the same gateway as eth0, otherwise change the above address accordingly

---

### Post by hgltqgs on 2007-04-26
thenk you

The problem continues I can not contact

The problem arose after updating

---

### Post by sdide on 2007-04-27
try 
~# dhclient eth1

if that does not give you an ip address, please post output of 

~# cat /etc/dhcp3/dhclient.conf | grep -v ^#

---

### Post by hgltqgs on 2007-04-27
I am sorry:( :( 

~# dhclient eth1

> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted


~# cat /etc/dhcp3/dhclient.conf | grep -v ^#
> 
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

---

### Post by hgltqgs on 2007-04-28
please help problem wifi

---

### Post by sdide on 2007-04-30
you need to run dhclient as root or with sudo.

---

### Post by hgltqgs on 2007-04-30
Thank you   ):P ):P :guitar:

---

