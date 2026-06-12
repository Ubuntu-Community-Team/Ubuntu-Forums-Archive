---
title: "iwlist eth1 scan: &quot; no scan results&quot;"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by checcouniud on 2008-03-09
Sorry if i ask your help,
but it is 1 year that I make fun of my roommate because he still uses windows, 
and now he is laughing because i am not able to set up the wireless.
I am not an expert!

I have just bought a router. I have configured it and my roomate is able to access it with not problems.

I have an inspiron 600 (year 2005) with ubuntu 7.10 installed
 
I played around a little bit but i have never seen any wireless. I may have mess up something installing and disinstalling  applications.


RESULTS FROM iwlist, ifconfig, iwconfig ARE


francesco@francesco-laptop:~$ iwlist eth1 scan
eth1      No scan results

francesco@francesco-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2gZvL885"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

francesco@francesco-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:71:8F:70  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe71:8f70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:276813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:143254282 (136.6 MB)  TX bytes:39279387 (37.4 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:0B:7D:15:98:F3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:11960 (11.6 KB)
          Interrupt:10 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:0B:7D:15:98:F3  
          inet addr:169.254.8.100  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:437799 (427.5 KB)  TX bytes:437799 (427.5 KB)

francesco@francesco-laptop:~$ 


THANK YOU SOO MUCH for any help

---

### Post by Hightide on 2008-03-09
Hi 

eth1      IEEE 802.11b/g  ESSID:"2gZvL885"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   

You are using a Broadcom 43xx driver and no connection (invalid),

Have a look at this [howto]("http://ubuntuforums.org/showthread.php?t=706034") 

and would recommend Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=596797")      

regards

:):)

---

### Post by checcouniud on 2008-03-09
THANK you A lot. But it seems that it did note fixedthe problem.
this is the new result:

francesco@francesco-laptop:~$ iwlist eth1 scan
eth1      No scan results

francesco@francesco-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

francesco@francesco-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:71:8F:70  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe71:8f70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101843 (99.4 KB)  TX bytes:38044 (37.1 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:0B:7D:15:98:F3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:dfdfe000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18125 (17.7 KB)  TX bytes:18125 (17.7 KB)

francesco@francesco-laptop:~$

---

