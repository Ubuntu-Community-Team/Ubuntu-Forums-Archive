---
title: "Ubuntu can't connect to ad-hoc network set on Vista"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by KORraN on 2007-11-28
Hi,
I have a little problem with Ubuntu. My friend has created an ad-hoc network and turn on network sharing. On WinXP there is no problem to connect this network (instead of that Vista is so stupid and once for a few hours it brakes down connection and there is no &^^%#$ way to connect again, so we have to create new network...). On my fresh-installed Ubuntu "iwlist scan" shows the Vista network but Linux is connecting so long and finally... it doesn't. I was googling about this problem and I found that wireless card should be in ad-hoc mode but there is an error:
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
```
Can anybody help me? Here are results of ifconfig and iwconfig:
```
korran@a69tc:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:16:CF:67:C4:72  
          inet6 addr: fe80::216:cfff:fe67:c472/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:6C:DD:39  
          inet addr:10.12.17.9  Bcast:10.12.17.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe6c:dd39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1809162 (1.7 MB)  TX bytes:259415 (253.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-67-C4-72-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4511 errors:0 dropped:0 overruns:0 frame:5847
          TX packets:3462 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:333222 (325.4 KB)  TX bytes:159108 (155.3 KB)
          Interrupt:18 

korran@a69tc:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"test"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=2/70  Signal level=-90 dBm  Noise level=-92 dBm
          Rx invalid nwid:654  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

---

### Post by spd106 on 2007-11-28
Have you installed the madwifi-tools package?

See [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) and the [http://madwifi.org](http://madwifi.org) website

---

### Post by roaldz on 2007-11-28
Network communication is based on IP adresses (at least in TCP/IP networks). If you connect to a network (you should see that as ¨pluggin in the cable¨) , make sure to get/set an IP adress.

---

