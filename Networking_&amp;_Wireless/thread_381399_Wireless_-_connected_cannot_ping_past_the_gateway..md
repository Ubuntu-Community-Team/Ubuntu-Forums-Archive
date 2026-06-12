---
title: "Wireless - connected cannot ping past the gateway. ??"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by jeremywho on 2007-03-10
I have a wrt54g connected to a cable modem.  I installed fiesty and can connect to the wrt54g no problem.  I can ping the router and the default gateway as well as connect to the router config webpage but I cannot ping any of the dns ip's or anyother address.  Everything looks good in the iwconfig output, managed mode, correct router mac address, etc.  I have no idea what to do from here!?  

Thanks!
-Jeremy

---

### Post by Mr. C. on 2007-03-10
Please show output from 

```
ifconfig -a
netstat -rn
```

and the IP, netmask, gateway from your router.

MrC

---

### Post by PilotJLR on 2007-03-10
In addition the the previous poster's questions, also try this:

```

sudo route add default gw (your gateway)

```

the address (your gateway) would probably be 192.168.1.1 or 192.168.0.1. it sounds like you already know what this is...

---

### Post by jeremywho on 2007-03-11
**ifconfig -a:**
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:67:E1:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:9C:0C:EA  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe9c:cea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:260 errors:1 dropped:1 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15254 (14.8 KiB)  TX bytes:12493 (12.2 KiB)
          Interrupt:20 Memory:e0206000-e0206fff 

eth0:avah Link encap:Ethernet  HWaddr 00:C0:9F:67:E1:56  
          inet addr:169.254.8.102  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:416 (416.0 b)  TX bytes:416 (416.0 b)


```

**netstat -rn**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0

```

My route has lan ip of 192.168.1.1, subnet 255.255.255.0.
You need to see the ip, subnet, gw that the router gets from the cable modem?

---

### Post by Mr. C. on 2007-03-11
You have 2 default routes (the last two are the default routes)

There should be only one default route, and it should be the address of your router's LAN interface.

Remove the gateway in /etc/network/interfaces for the interface that does not go to your router.

MrC

---

### Post by jeremywho on 2007-03-11
I disabled a wired interface in the network control panel and now there is only one default route, but I am getting the same behavior as before.  Here's the new outputs:

**ifconfig:**
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:67:E1:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:9C:0C:EA  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe9c:cea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1136 errors:1 dropped:1 overruns:0 frame:0
          TX packets:890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:306079 (298.9 KiB)  TX bytes:83175 (81.2 KiB)
          Interrupt:20 Base address:0x6000 Memory:e0206000-e0206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


```

**netstat:**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1

```


thanks for the help btw!!

---

### Post by bukwirm on 2007-03-11
Some routers need to have the DNS servers set manually (instead of automatically detected) - try it.
Also, some DNS servers have problems with IPv6 - look at [this post]("http://ubuntuforums.org/showthread.php?t=282034").

---

### Post by Mr. C. on 2007-03-11
Your route table still has on unused route.  It has a automatic private IP address, which is only used if no IP has been assigned.  This could be removed from the route table, but is harmless otherwise.

Just to be sure we're all on the same page, you are saying that you cannot ping any IP addresses  (eg.not names) besides 192.168.1.1, correct ?

MrC

---

