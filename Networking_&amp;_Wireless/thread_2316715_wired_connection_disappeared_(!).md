---
title: "wired connection disappeared (?!)"
date: 2016-03-10
forum: Networking &amp; Wireless
---

### Post by gianluca3 on 2016-03-10
hello,

yesterday my wired connection suddenly disappeared. I don't know very well how to explain the behavior, my network connection shows the following screenshot (attached). Apparently I do not see anymore the auto ethernet option. If I select "edit connection" the auto ethernet input is there unchanged.
 
```
 
ifconfig
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4475345 (4.4 MB)  TX bytes:4475345 (4.4 MB)


lxcbr0    Link encap:Ethernet  HWaddr 32:2d:8a:53:3c:c9  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::302d:8aff:fe53:3cc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:97517 (97.5 KB)


virbr0    Link encap:Ethernet  HWaddr 5e:b1:ec:b1:a4:52  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr e8:b1:fc:41:49:e3  
          inet addr:10.51.13.47  Bcast:10.51.15.255  Mask:255.255.240.0
          inet6 addr: fe80::eab1:fcff:fe41:49e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:428399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24730332 (24.7 MB)  TX bytes:627494749 (627.4 MB)

``` 
   
```

dmesg | grep virb
[    5.283693] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready

```

any suggestion? any idea why the interface eth0 disappeared and now there is a virbr0 one?

---

### Post by gianluca3 on 2016-03-10
[SIZE=4][FONT=arial]addition: I erased virbr0 and  lxcbr0
then I added the following two lines in /etc/network/interfaces:

```

auto eth0
iface eth0 inet dhcp

```
and this blocked the whole networking, running ifconfig only showed lo... [/FONT][/SIZE]

---

### Post by gianluca3 on 2016-03-10
[SIZE=4][FONT=arial]addition: I erased virbr0 and  lxcbr0
then I added the following two lines in /etc/network/interfaces:

[CODE]
auto eth0
iface eth0 inet dhcp
[\CODE]
and this blocked the whole networking, running ifconfig only showed lo... [/FONT][/SIZE]

---

### Post by gianluca3 on 2016-03-10
well... the ethernet port was connected to a usb replicator. it has been sufficient to unplug and plug the power to this device...

i was stupidly trying to configure a non existent eth0 port

---

