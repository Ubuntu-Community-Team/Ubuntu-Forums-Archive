---
title: "Wired &amp; Wireless problems"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by Fale on 2008-03-15
Hmm... where I should start. Well I'm newcomer from windows world. I have fresh 7.10 install on my laptop. I have configured VirtualBox 1.5.6 Host Interface to work. I think I have done something wrong there when I messed with network and I can't figure how I can fix it or "reset" network config. So I ask for your help.

**Problems:**

Wired network is not working. (VirtualBox Windows XP and Vista network works perfectly.) After boot I do not get IP address automatically. I have to do: **sudo dhclient eth0**. Now eth0 have ip, but it not still work. example if I ping google:

**ping:**
```
PING google.fi (216.239.59.104) 56(84) bytes of data.
From prfzltvt.local (10.0.0.5) icmp_seq=2 Destination Host Unreachable
From prfzltvt.local (10.0.0.5) icmp_seq=3 Destination Host Unreachable
From prfzltvt.local (10.0.0.5) icmp_seq=4 Destination Host Unreachable
```

**ifconfig** Here you can see that I have "Vbox0" virtual network card for VirtualBox which is bridged with eth0. eth1 is my wireless
```
br0       Link encap:Ethernet  HWaddr 00:17:08:3F:2D:39  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe3f:2d39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:252637657 (240.9 MB)  TX bytes:15510079 (14.7 MB)

eth0      Link encap:Ethernet  HWaddr 00:17:08:3F:2D:39  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255922000 (244.0 MB)  TX bytes:16157842 (15.4 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:0B:8C:CC  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe0b:8ccc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1468 errors:1 dropped:2126 overruns:0 frame:0
          TX packets:2346 errors:0 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000 
          RX bytes:14754601 (14.0 MB)  TX bytes:5722935 (5.4 MB)
          Interrupt:16 Memory:e8000000-e8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6296 (6.1 KB)  TX bytes:6296 (6.1 KB)

vbox0     Link encap:Ethernet  HWaddr 00:FF:F4:CC:BE:7D  
          inet6 addr: fe80::2ff:f4ff:fecc:be7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:232 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

**Wireless:**
Wireless seems to work ok. When I activate wireless I get IP and everything works. BUT, if I unplug my wired (eth0) I lose my connection... weird. Seems that my wireless is bridged some how to my wired connection...


Easy way to fix this might be to "reinstall" or "reset" whole networking to defaults, how to do it? Other way is to troubleshoot this mess. I bet I have to give more information, but don't know what... just ask and I provide more.

Thank you.

---

### Post by spd106 on 2008-03-15
As you can resolve google.fi you do have a connection and DNS is working. This means that you do probably have a routing issue.

I'm not very familiar with bridged interfaces, but I think the brctl tool might yield some useful information.

So check output of these commands
```
ip r
brctl show br0
```

---

### Post by Fale on 2008-03-16
Yes, it seems that DNS is working because it resolves google.fi IP address.

Those commands:

**ip r** (eth0)
```
10.0.0.0/24 dev br0  proto kernel  scope link  src 10.0.0.5 
10.0.0.0/24 dev eth0  proto kernel  scope link  src 10.0.0.5 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 10.0.0.2 dev eth0 
default via 10.0.0.2 dev br0  metric 100 
```

**ip r** (eth1)
```
10.0.0.0/24 dev br0  proto kernel  scope link  src 10.0.0.5 
10.0.0.0/24 dev eth1  proto kernel  scope link  src 10.0.0.6 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 10.0.0.2 dev eth1 
default via 10.0.0.2 dev br0  metric 100 
```


**brctl show br0** 
```
bridge name     bridge id               STP enabled     interfaces
br0             8000.0017083f2d39       no              eth0
                                                        vbox0
```

---

### Post by Fale on 2008-03-16
Update:

It takes very long time to boot if wired is unplugged, but when finally ubuntu loads Wireless works fine. If I now plug Wired and then unplug it wireless stops to work.

**Right after boot route -n** (Wireless on and Wired off)
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 br0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth1
0.0.0.0         10.0.0.2        0.0.0.0         UG    100    0        0 br0
```

**Wired plugged route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 br0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG    100    0        0 br0
```

**Wired unplugged and wireless in use route -n** (Network not work)
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 br0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth1
0.0.0.0         10.0.0.2        0.0.0.0         UG    100    0        0 br0
```

---

