---
title: "WAN yes, LAN no?"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by MoreCalories on 2008-06-15
This problem literally just popped up a few hours ago after I ran some updates. I've tried troubleshooting, but I can't figure this out. I can ping anything on the WAN (google), but can't ping anything internal, and anything internal can't ping my computer, showing no route to host. The host cmoputer shows "Destination Host Unreachable." I'd appreciate any help, as my guess is some sort of routing issue.

ifconfig:
```

ath0      Link encap:Ethernet  HWaddr 00:11:6b:62:25:e7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe62:25e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7724 errors:97 dropped:97 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9959207 (9.4 MB)  TX bytes:904708 (883.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51754 (50.5 KB)  TX bytes:51754 (50.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-6B-62-25-E7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38404 errors:0 dropped:0 overruns:0 frame:13959
          TX packets:8358 errors:0 dropped:97 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:16421664 (15.6 MB)  TX bytes:1236168 (1.1 MB)
          Interrupt:11 

```

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 ath0


```

Network interfaces:
```

auto lo
iface lo inet loopback

#auto eth0

#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

auto ath0

iface ath0 inet dhcp
wpa-psk blah blah
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid MNHA3
```

---

### Post by MoreCalories on 2008-06-15
A reboot of my router(Actiontec) fixed this. Any ideas?

---

