---
title: "Fluxbox and ndiswrapper wireless not loading on startup"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Aurix on 2008-04-03
**EDIT: Oops! didn't read the sticky, and I've fixed it now. sorry!**

Hello,

I'm running Ubuntu 7.10, ndiswrapper 1.43, and fluxbox 1.0.0.

I've been wanting to try something different than gnome, so, I chose fluxbox, and am enjoying it so far. My only problem is that when I load fluxbox it doesn't connect to my wireless network. I have ndiswrapper setup and working, and if I load gnome, and then go back to fluxbox, my wireless network is connected. The wireless network is open.

This is what I've got so far: (taken from a terminal within fluxbox without starting gnome first)
```

comrade@lunix:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

comrade@lunix:~$ sudo iwconfig wlan0 essid "linksys"
[sudo] password for comrade:
comrade@lunix:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:10:A9:0D:E9   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:875  Invalid misc:4677   Missed beacon:0

comrade@lunix:~$ sudo ifconfig wlan0 up
comrade@lunix:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7E:E5:AE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:C1:00:96:7A  
          inet6 addr: fe80::214:c1ff:fe00:967a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:789 (789.0 b)  TX bytes:468 (468.0 b)
          Interrupt:18 Memory:fdefe000-fdf00000 

comrade@lunix:~$ ping 192.168.15.1
connect: Network is unreachable

```

and this is taken from a terminal in gnome:
```

comrade@lunix:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7E:E5:AE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:C1:00:96:7A  
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::214:c1ff:fe00:967a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2591495 (2.4 MB)  TX bytes:510338 (498.3 KB)
          Interrupt:18 Memory:fdefe000-fdf00000 

comrade@lunix:~$ ping 192.168.15.1
PING 192.168.15.1 (192.168.15.1) 56(84) bytes of data.
64 bytes from 192.168.15.1: icmp_seq=1 ttl=255 time=15.7 ms
64 bytes from 192.168.15.1: icmp_seq=2 ttl=255 time=13.6 ms
64 bytes from 192.168.15.1: icmp_seq=3 ttl=255 time=9.37 ms

--- 192.168.15.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 9.377/12.925/15.792/2.662 ms

```

Any ideas on how to fix this, and edit fluxbox's startup script so it connects automatically?

---

