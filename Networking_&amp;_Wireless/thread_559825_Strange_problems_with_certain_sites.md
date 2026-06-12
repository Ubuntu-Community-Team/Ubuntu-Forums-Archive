---
title: "Strange problems with certain sites"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by mrodriguez on 2007-09-25
Ok, everything works for me fine on the internet.. however two things don't.

1. I cant send attachments in gmail, the page never finishes loading (or gives error that it isnt found in opera)

2. I cant login to commonapp.org, the page never finishes loading (or gives error that it isnt found in opera)

Both problems in firefox and opera so im guessing its the os.

results for ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:15:F2:EF:80:F3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0D:88:E5:BD:B3  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2822461 (2.6 MiB)  TX bytes:722325 (705.3 KiB)
          Interrupt:21 Memory:fe5ffc00-fe5ffc25 

```

results for netstat -rn
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

```

/etc/hosts and /etc/resolv.conf

```

127.0.0.1       localhost
127.0.1.1       mauricio-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
nameserver 201.217.1.230
nameserver 201.217.1.231

```

If anything else is needed please ask. Thanks!

---

### Post by noob12 on 2007-09-25
You might try this and see if it helps:

[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

