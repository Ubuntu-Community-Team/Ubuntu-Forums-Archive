---
title: "internet disconnets after ~1 min."
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by jjbird on 2006-09-03
I just recently did an install of the dapper server on an older computer I have, and after much searching the internet was able to figure out how to configure my ethernet card from the terminal (im relatively new to the linux command line).  now i can connect to computers on my local network (i can ping them and can ssh into the server that is having problems) but when i try to connect to the internet i have to run "sudo dhclient eth0", it then will connect for about a minute before not being able to connect to anything outside my local network.  Also when it stops connecting to the internet I can no longer ping my router/gateway.  Im pretty sure that ive got the gateway settings configured properly but its possible that i did something wrong configuring them.  any help would be appreciated.

various information if this helps

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:0C:08:C7  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe0c:8c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16336001 (15.5 MiB)  TX bytes:1633589 (1.5 MiB)
          Interrupt:3 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13488 (13.1 KiB)  TX bytes:13488 (13.1 KiB)
```
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0


```
```

$ vi /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

auto eth0
iface eth0 inet dhcp
name Ethernet LAN card

dns-nameservers 192.168.1.254

# The loopback network interface
auto lo
iface lo inet loopback
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/network/interfaces" [readonly] 12L, 290C   
```

Thanks in advance

---

### Post by jjbird on 2006-09-03
Okay, I figured it out, boy do I feel stupid now, I had another computer on my network trying to get the same ip.  Sorry to bother yall.

---

