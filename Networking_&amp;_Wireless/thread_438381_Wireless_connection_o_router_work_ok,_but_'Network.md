---
title: "Wireless connection o router work ok, but 'Network Unreachable'."
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by dave_gr on 2007-05-09
I've configured a wpa wireless link to my router and it says I have connected - with a graphic at the top telling me the signal level/status etc.

However when I open firefox I can't see the internet.  Pinging my router (192.168.254.254) produces 'network unreachable' and I don't know what to do.   Here's some statements I ran - can anyone figure this out for me?

Many thanks in advance!

David


--------------------------------------------------------------------------
iwconfig:
--------------------------------------------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Emerald"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:90:96:CD:81:81   
          Bit Rate:48 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/94  Signal level=-53 dBm  Noise level=-87 dBm
          Rx invalid nwid:1095  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


--------------------------------------------------------------------------
ifconfig:
--------------------------------------------------------------------------

ath0      Link encap:Ethernet  HWaddr 00:12:BF:5F:2A:AA  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:bfff:fe5f:2aaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3863 (3.7 KiB)  TX bytes:6610 (6.4 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0E:A6:6C:24:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth0:avah Link encap:Ethernet  HWaddr 00:0E:A6:6C:24:84  
          inet addr:169.254.5.195  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:618 (618.0 b)  TX bytes:618 (618.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-12-BF-5F-2A-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2655 errors:0 dropped:0 overruns:0 frame:3781
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:308369 (301.1 KiB)  TX bytes:20193 (19.7 KiB)
          Interrupt:17

---

### Post by chili555 on 2007-05-09
I don't believe your router is 192.168.254.254. It may be 192.168.1.254 or something else entirely. Does```
route -n
```tell you the gateway, which is the IP of your router?

---

### Post by dave_gr on 2007-05-10
Hi chili,

Here's the results of route -n

>sudo route -n

Kernel IP routeing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 ath0
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 ath0
0.0.0.0 0.0.0.0 0.0.0.0 U 1000 0 0 eth0

---

### Post by chili555 on 2007-05-10
Please try the following:```
ping -c3 192.168.1.1
ping -c3 192.168.1.254
ping -c3 72.14.209.104
cat /etc/resolv.conf
```Thanks.

---

### Post by dave_gr on 2007-05-10
~$> ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.65 icmp_seq=1 Destination Host Unreachable
From 192.168.1.65 icmp_seq=2 Destination Host Unreachable
From 192.168.1.65 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
~$> ping -c3 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=1.96 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=1.35 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=1.34 ms

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 1.343/1.553/1.967/0.294 ms
~$> ping -c3 72.14.209.104
connect: Network is unreachable
~$> ping [www.google.com](www.google.com)
connect: Network is unreachable
~$> cat /etc/resolv.conf 
# generated by NetworkManager, do not edit!

search lan


nameserver 192.168.1.254


~$>

---

### Post by chili555 on 2007-05-10
You are getting to the router, with nice, quick times, but not the outside world. So the router, 192.168.1.254, is not getting an IP address from your cable- or DSL-modem, it appears. As a first step, I would power-cycle both the modem and router by unplugging the modem and the router, plug the modem back in and wait for the LED's to tell you it has a signal from your provider, then plug in the router and wait for it to stabilize as well. Then try the pings I outlined above. 

Your /etc/resolv.conf looks unusual, but should work fine.

---

### Post by dave_gr on 2007-05-11
Have tried this - still not working.

My DSL provider gives me a static IP address so do I need to tell Linux what this is to route correctly?

NB WinXP works fine and is seeing the internet as expected.

Thanks Again,

David

---

### Post by javahollic on 2007-05-15
I just hit this today, I finally got BCM4306 wireless/Ubuntu feisty hooked up to a known good cable modem and netgear WGT624 wireless router (Im using it now via an XP box).

I can ping my wireless router (192.168.1.1) but I get Destination Unreachable with any external address (yet the DNS resolution is working fine).

my /etc/resolv.conf has 1line : nameserver 192.168.1.1

route -n yields:
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0    0.0.0.0           255.255.255.0   U     0      0        0 eth1
169.254.0.0    0.0.0.0           255.255.0.0     U     1000   0        0 eth1
0.0.0.0            0.0.0.0           0.0.0.0             U     0      0        0 eth1
0.0.0.0          192.168.1.1     0.0.0.0            UG    0      0        0 eth1

Ive already disabled IP6 (added 'blacklist ipv6' to /etc/modules.d/blacklist) so thats not it.  I dont get where the 169.254.0.0 entry is coming from, it seems to have a high metric, perhaps that is defaulting to the route.  Ive rebooted a bunch of times and its still there.

:confused:

---

### Post by javahollic on 2007-05-15
I had a can't ping Internet hosts (routing issues).

I found a post that gave me the followin *temporary* fix, that can be applied in /etc/rc.local until somebody figures out the correct way to do it, namely:

#!/bin/bash
# zaps the 169 route, resets to use my wireless router on eth1
#
ip r d default dev eth1
ip r d 169.254.0.0./16
ip r a default via 192.168.1.1 dev eth1

ad, lo, I have Synaptic updates.:guitar:

---

