---
title: "Wireless Connection Painfully Slow with new install of 8.10"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by Boffy on 2008-04-22
Hey Guys,

I've just installed 8.10 and the internet is really slow (~24kbps norm~500kbps). I've tried a few fixes and they don't work (i.e. this one: [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744))

I'm really struggling here and would like some help. Here are some key files:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:0f:f3:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44300 (43.2 KB)  TX bytes:44300 (43.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:a8:55:26  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fea8:5526/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10494863 (10.0 MB)  TX bytes:1427731 (1.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-A8-55-26-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

/etc/hosts

```
127.0.0.1 localhost
127.0.0.1 main-server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.1.1 main-server.localhost
```

/etc/resolv.conf

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4721
#
### END INFO

search Belkin

nameserver 192.168.2.1

```


Regards,

---

### Post by echolink on 2008-11-02
> **Boffy said:**
> Hey Guys,

I've just installed 8.10 and the internet is really slow (~24kbps norm~500kbps). I've tried a few fixes and they don't work (i.e. this one: [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744))

I'm really struggling here and would like some help. Here are some key files:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:0f:f3:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44300 (43.2 KB)  TX bytes:44300 (43.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:a8:55:26  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fea8:5526/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10494863 (10.0 MB)  TX bytes:1427731 (1.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-A8-55-26-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

/etc/hosts

```
127.0.0.1 localhost
127.0.0.1 main-server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.1.1 main-server.localhost
```

/etc/resolv.conf

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4721
#
### END INFO

search Belkin

nameserver 192.168.2.1

```


Regards,

I have a **Linksys WUSB54G USB adapter**. I was having a really slow connection using the **rt73usb driver** that was default for Ibex, I origionally **disabled ipv6** in **etc/modprobe.d/aliasis**, and **firefox using about:config**. I was getting alot of errors upon review of ifconfig. I ended up installing **ndiswrapper** and changed from **rt73usb**, to the **windows xp/2x rt73 driver** from my install CD. From there in went in and **reenabled IPV6 In firfox, and etc/modprobe.d/aliasis**. Once all was complete it worked with a solid connetction, with speed. Im not sure if this process will work for you, but hey its worth a shot.

---

