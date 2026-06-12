---
title: "Embroiled in wireless issues"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by waitingbeckett on 2009-07-13
Having self-exiled myself from XP, I'm an Ubuntu newb. The transition has not been too difficult thanks to the myriad of forums for people like me. But, wireless remains very vexing. 
 
After the initial install, my wireless network was immediately recognized. However, not long after, the connection dropped often, and, eventually I was not able to connect to it. I am only able to access my wireless when the laptop is right next to the router. Even then, it is not consistent. I never had any issues with coverage under XP.
 
I've read a lot about drivers, but am not sure how to best address it. I use an Atheros Card in a Thinkpad T61. 
 
 
Thanks

---

### Post by waitingbeckett on 2009-07-13
Here is the results from the commands suggested in another thread. I did all of these while having a connection active. I imagine it might be different if I did it while I was having my problems with it. 

**ifconfig:**

ath0      Link encap:Ethernet  HWaddr 00:19:7e:34:a7:0c  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe34:a70c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10247399 (10.2 MB)  TX bytes:1293109 (1.2 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:58:83:a8:f9  
          inet6 addr: fe80::215:58ff:fe83:a8f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:23501465 (23.5 MB)  TX bytes:1451028 (1.4 MB)
          Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99244 (99.2 KB)  TX bytes:99244 (99.2 KB)

pan0      Link encap:Ethernet  HWaddr 0a:f2:97:cc:2c:98  
          inet6 addr: fe80::8f2:97ff:fecc:2c98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:120748 (120.7 KB)

pan0:avahi Link encap:Ethernet  HWaddr 0a:f2:97:cc:2c:98  
          inet addr:169.254.8.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wifi0     Link encap:UNSPEC  HWaddr 00-19-7E-34-A7-0C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152458 errors:0 dropped:0 overruns:0 frame:4128
          TX packets:23083 errors:1718 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:33250116 (33.2 MB)  TX bytes:2633601 (2.6 MB)
          Interrupt:17 
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:FF:0E:A8   
          Bit Rate:2 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-37 dBm  Noise level=-95 dBm
          Rx invalid nwid:24113  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 pan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
[B]
ping -c 3 208.67.219.101[/B]

PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.
64 bytes from 208.67.219.101: icmp_seq=1 ttl=47 time=86.2 ms
64 bytes from 208.67.219.101: icmp_seq=2 ttl=47 time=93.1 ms
64 bytes from 208.67.219.101: icmp_seq=3 ttl=47 time=93.5 ms

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2

**ping -c 3 [www.opendns.com](www.opendns.com)**

PING [www.opendns.com](www.opendns.com) (208.67.219.99) 56(84) bytes of data.
64 bytes from [www.opendns.com](www.opendns.com) (208.67.219.99): icmp_seq=1 ttl=48 time=86.9 ms
64 bytes from [www.opendns.com](www.opendns.com) (208.67.219.99): icmp_seq=2 ttl=48 time=87.0 ms
64 bytes from [www.opendns.com](www.opendns.com) (208.67.219.99): icmp_seq=3 ttl=48 time=86.6 ms

--- [www.opendns.com](www.opendns.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 86.634/86.903/87.083/0.193 ms

---

### Post by waitingbeckett on 2009-07-14
Maybe there is a better forum for this? Or am just being too impatient?

---

### Post by vruum on 2009-07-14
Have you tried connecting to other acces points? I'm not ruling out that there could be problems with the driver, but I've seen similar behavior caused by some routers, in those cases a reboot or reset of the router fixed it.

---

### Post by waitingbeckett on 2009-07-14
No, I have not been able to try other access points. It seems like ubuntu is just having problems finding the signal and therefore connecting in other rooms, whereas Vista is not having this problem.

---

### Post by waitingbeckett on 2009-07-15
I guess I'll keep plugging away for a few more days before switching back to Windows. 

I read a post in which someone found more luck in switching to Kwifimanager. Can someone explain to me how I would go about doing this?

---

