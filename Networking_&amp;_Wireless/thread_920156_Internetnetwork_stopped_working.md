---
title: "Internet/network stopped working"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by shud on 2008-09-15
Hey guys 

Installed Ubuntu the other day...my internet ran fine for a short time but now it simply will not connect to the internet. However, inside an XP Virtual Machine, there is a network connection with no issues. :confused:

I ran the hardware test and when it got to my onboard NVIDIA NIC, this is what I got: 

```
ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
    sys.exit(main(sys.argv[1:]))
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main
    host = route.get_default_gateway()
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
    t1 = self._get_default_gateway_from_bin_route()
  File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route
    if def_gateway:
UnboundLocalError: local variable 'def_gateway' referenced before assignment

Are you connected to the Internet?

```

Here is my ifconfig: 

```
eth0      Link encap:Ethernet  HWaddr 00:21:85:03:03:8a  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe03:38a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2460566 (2.3 MB)  TX bytes:233105 (227.6 KB)
          Interrupt:250 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99720 (97.3 KB)  TX bytes:99720 (97.3 KB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I can ping my gateway at 192.168.1.1, but nothing else. :(

I have no idea what to do at this point. My internet connection worked fine for about 6 hours and then just quit.

---

