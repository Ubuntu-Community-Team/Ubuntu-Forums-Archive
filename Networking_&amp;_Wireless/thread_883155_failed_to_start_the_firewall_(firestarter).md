---
title: "failed to start the firewall (firestarter)"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by joeboentoe on 2008-08-07
The situation:

I had a bridged configuration with br0, but I deleted br0 and now I only have eth0 and l0 left. This works fine exept for the firewall who keeps saying:


failed to start the firewall
the device br0 is not ready

please check your network device settings and make sure your internet connection is active

so I did a bit searching and in the /etc/firestarter/configuration is this

```
# --(External Interface)--
# Name of external network interface
IF="br0"
# Network interface is a PPP link
EXT_PPP="off"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth0"
```

now; if I change it to

```
# --(External Interface)--
# Name of external network interface
IF="eth0"
# Network interface is a PPP link
EXT_PPP="off"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth0"
```

firestarter starts up fine but when I try to change the outbound from restricted to permissive or when I try to change the view from outbound to inbound rules, firestarter automaticly edits his configuration file and puts it back to

```
# --(External Interface)--
# Name of external network interface
IF="br0"
# Network interface is a PPP link
EXT_PPP="off"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth0"
```

So why does firestarter thinks there is still a br0?

for more info
```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:17:44:ff:b7  
          inet addr:192.168.0.188  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe44:ffb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2855206 (2.7 MB)  TX bytes:417950 (408.1 KB)
          Interrupt:250 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114576 (111.8 KB)  TX bytes:114576 (111.8 KB)
```


thanks

---

