---
title: "Setting static ip address on eth0 causes wlan0 to lock"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by biasedopiniondrummer on 2008-06-21
hey guys! its been a while! ok, i just installed a new motherboard in my computer and installed a wireless card (rtl8185 chipset) and did a fresh installation of ubuntu hardy. I'm trying to share my internet connection with a laptop via crossover cable. 

here is my set up:

I'm getting wireless via wlan0 on my rtl8185 using [this driver and patch]("http://www.willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy") (which worked great by the way).  i'm trying to share the connection with a laptop via eth0 on the desktop connected to eth0 on my laptop (also running ubuntu). When following this [tutorial]("http://ubuntuforums.org/showthread.php?t=91370") I was unable to connect to access the internet on my desktop (wireless). 

basically anytime i specify a static ip on eth0 the i cannot access the internet (although wlan0  still shows that it is connected to the network)

any thoughts? thanks

Clay

---

### Post by unutbu on 2008-06-21
Please run (and post the output of)
```

route
ifconfig
```
on both your desktop and your laptop.

---

### Post by biasedopiniondrummer on 2008-06-21
i should mention that i changed back the static ip on the desktop.

```
Kernel IP routing table
Destination     Gateway      Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *            255.255.254.0   U     0      0       0 wlan0
link-local      *            255.255.0.0     U     1000   0       0 wlan0
default         192.168.0.1  0.0.0.0         UG    0      0       0 wlan0 


eth0      Link encap:Ethernet  HWaddr 00:1e:8c:82:c7:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90200 (88.0 KB)  TX bytes:90200 (88.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:31:60:37  
          inet addr:192.168.1.156  Bcast:192.168.1.255  Mask:255.255.254.0
          inet6 addr: fe80::214:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162396 errors:1032 dropped:1420 overruns:0 frame:0
          TX packets:134055 errors:100 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225851332 (215.3 MB)  TX bytes:14307808 (13.6 MB)
          Interrupt:20 Memory:ffffc200008ca000-ffffc200008ca100 
 
```

laptop: (and the problem happens whether the  laptop is connected or not, it seems to happen any time i set a static ip)

```

Kernel IP routing table
Destination     Gateway      Genmask         Flags Metric Ref    Use Iface
link-local      *            255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *            255.255.0.0     U     0      0        0 eth0
default         192.168.0.1  0.0.0.0         UG    100    0        0 eth0


eth0      Link encap:Ethernet  HWaddr 00:90:f5:2b:89:6a  
          inet addr:192.168.0.2  Bcast:192.168.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64341 (62.8 KB)  TX bytes:64341 (62.8 KB)
```

---

### Post by unutbu on 2008-06-21
biasedopiniondrummer, I am not an expert on networking issues, so I could be wrong about my diagnosis and solution. However, on the off chance that I am right, here are some thoughts:

The desktop's routing table says


```

Destination     Gateway      Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *            255.255.254.0   U     0      0       0  wlan0
```
which means all packets destined for 192.168.0.* or 192.168.1.* should be sent through the wlan0 interface. 

The laptop's routing table says 

```

Destination     Gateway      Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *            255.255.0.0     U     0      0        0 eth0

```
and this means all packets destined for 192.168.*.* should be sent through the eth0 interface.

When you assign a static ip for eth0 on the desktop, I suspect you are (indirectly) adding a routing table entry of the form
```

Destination     Gateway      Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *            255.255.0.0     U     0      0        0 eth0
```

which contradicts the first routing table entry I mentioned above. This would tell the desktop that all packets destined for the 192.168.*.* network be sent through eth0. Unfortunately, your router has address 192.168.0.1, so all packets that were intended for the router are now being sent down eth0's cable and not getting to the router.

The fix is to segregate packets destined for the wlan0 network from those destined for the eth0 network. See the attached figure, below.

1) Keep wlan0 the way it is (It's working, so I'll try not to touch it).
   wlan0's network is 192.168.0.* and 192.168.1.*. (network mask 255.255.254.0)
   This is the way things are already set up, so there's nothing new here that needs to be done.

2) Assign eth0 on the desktop the ip address 192.168.2.1. eth0's network is 192.168.2.* (network mask 255.255.255.0). Either set this up using a GUI (network manager, wicd, or whatever), or run the command

On desktop:
```
sudo ifconfig eth0 192.168.2.1 netmask 255.255.255.0 up
```

3) Assign eth0 on the laptop the ip address 192.168.2.2. eth0's network is 192.168.2.* (network mask 255.255.255.0). Again, use a GUI or run the command

On laptop:
```
sudo ifconfig eth0 192.168.2.2 netmask 255.255.255.0 up
```

---

### Post by biasedopiniondrummer on 2008-06-22
hey, thanks for the quick reply and for the well-thought answer. I'm gonna give it a shot and then repost my results

---

### Post by biasedopiniondrummer on 2008-06-22
ok! it worked! thanks! that was the problem

---

