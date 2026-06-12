---
title: "Wireless connected _but_ 'Network is unreachable'"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by dave_gr on 2007-05-09
Hi,

I have successfully connected to a wireless router using howtos on this site (was WPA) but when I load Firefox I can't see anything.  The network is talking to some DNS server though so I can't figure this out:

#>ping [www.amazon.com](www.amazon.com)
PING [www.amazon.com](www.amazon.com) (72.21.210.11) 56(84) bytes of data.
From home-pc.local (169.254.5.195) icmp_seq2 Destination Host Unreachable
From home-pc.local (169.254.5.195) icmp_seq2 Destination Host Unreachable
...

No idea how to fix and have searched many forums for ideas.  Best I can do is post the command responses other people post (I don't really understand them to be honest):


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


--------------------------------------------------------------------------
sudo route -n
--------------------------------------------------------------------------
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0


Help!!!


David

---

### Post by rgraves22 on 2007-05-09
What kind of wireless card do you have?

---

### Post by dave_gr on 2007-05-09
Belkin Wireless G Desktop Card F5D7000

---

