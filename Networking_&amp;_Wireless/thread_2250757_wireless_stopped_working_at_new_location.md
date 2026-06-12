---
title: "wireless stopped working at new location"
date: 2014-10-30
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2014-10-30
My wireless has stopped connecting I  am pasting the output  of ifconfig and iwconfig. I can't connect to any wireless even though they are seen by the network manager. The ifconfig sees the wireless and the iwconfig doesn't. I need to get this working, thanks I am getting the same results with 2 different working routers
```

cmcanulty@ubuntu1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:4a:92:03:35:c1  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3e4a:92ff:fe03:35c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24374 (24.3 KB)  TX bytes:79754 (79.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107255 (107.2 KB)  TX bytes:107255 (107.2 KB)

wlan0     Link encap:Ethernet  HWaddr 90:00:4e:1f:17:8b  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe1f:178b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:1256
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18251 (18.2 KB)  TX bytes:41182 (41.1 KB)
          Interrupt:18 

cmcanulty@ubuntu1:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:DB:45:4F   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
cmcanulty@ubuntu1:~$ 
```

---

### Post by weatherman2 on 2014-10-30
The output of those two commands shows you are connected to a wireless access point called "linksys" and that you have an IP address of 192.168.1.101 .

What doesn't work exactly?

---

### Post by cmcanulty on 2014-10-30
no wireless though it shows in the network connections as a strong signal won't connect except by ethernet

---

