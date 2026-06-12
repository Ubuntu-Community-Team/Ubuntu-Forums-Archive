---
title: "failed to bring up eth0"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Squizz on 2008-03-01
Hi guys, it seems as though there's something different wrong with my ubuntu daily. I've recently done a full clean install, and the internet was working just fine with a static ip and port 80 traffic forwarding to my server (on the same computer).

The internet works fine on the other machines on my network, but on my main one 192.168.1.1 now points to my server as well instead of my router control panel.

Here's some information that will hopefully help;

```

root@server1:~# /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                 
SIOCADDRT: No such process 
Failed to bring up eth0. 
                                                                         [ OK ] 

```

```

root@server1:~# ping 64.233.187.99 
connect: Network is unreachable 

```

```

root@server1 cat /etc/network/interfaces

auto lo 
iface lo inet loopback 
 
iface eth0 inet static 
address 192.168.1.99 
netmask 255.255.255.0 
gateway 192.168.1.1 
 
auto eth0

```

```

127.0.0.1 localhost 
192.168.1.1 all.my.websites
 
::1 ip6-localhost ip6-loopback server1.mysite.com
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 

```

```

root@server1:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:DB:F6:58:C9   
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:20 Base address:0xe000  
 
eth1      Link encap:Ethernet  HWaddr 00:19:DB:F7:DF:4D   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:20  
 
eth2      Link encap:Ethernet  HWaddr 00:16:E3:46:70:C4   
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:e3ff:fe46:70c4/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1115 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2449 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:281090 (274.5 KB)  TX bytes:212229 (207.2 KB) 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:703 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:703 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:56489 (55.1 KB)  TX bytes:56489 (55.1 KB) 
 
vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01   
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08   
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

```

Everything was working fine until I rebooted, when everything sort of died!

Thanks for your help!

---

