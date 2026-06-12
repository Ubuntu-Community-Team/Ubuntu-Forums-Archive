---
title: "weird network behavior"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by martbab on 2007-10-01
Hello everyone,

I have a very strange problem with network on my notebook running under Xubuntu Linux. I am connected to wired network via DHCP, but if I don't use internet for awhile the connection dies out...seems like the DHCP server of my ISP doesn't renew my IP address, I'm not very much into network issues, so I'm just guessing.

When I run "sudo dhclient" to request IP address nothing happens, I have to retype the command several types until the connection starts working and after few minutes the it dies again. The interesting thing is that Gaim continues to run without any error, I can send and receive IMs without any problems.

I have no idea if it is Xubuntu problem or something is wrong with my ISP.

here's the output of "ifconfig" and "/etc/network/interfaces"

eth0      Link encap:Ethernet  HWaddr 00:14:38:10:3D:F1  
          inet addr:147.251.214.67  Bcast:147.251.214.255  Mask:255.255.255.0
          inet6 addr: fe80::214:38ff:fe10:3df1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:613381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:403796598 (385.0 MiB)  TX bytes:6081531 (5.7 MiB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:F8:79:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Memory:d0000000-d0002000 

eth1:avah Link encap:Ethernet  HWaddr 00:90:4B:F8:79:68  
          inet addr:169.254.7.251  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Memory:d0000000-d0002000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9261661 (8.8 MiB)  TX bytes:9261661 (8.8 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.24.128  Bcast:172.16.24.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.173.128  Bcast:192.168.173.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp
address 147.251.214.67
netmask 255.255.255.0
gateway 147.251.4.3

I'd be happy if someone could help me! And sorry for the lenght of my post :)

---

### Post by cameronjcc on 2007-10-01
Are you using a direct DHCP or a Router?  It sounds like DHCP Direct, but you could be using your router as a bridge.  Let me know.

---

### Post by martbab on 2007-10-01
> **cameronjcc said:**
> Are you using a direct DHCP or a Router?  It sounds like DHCP Direct, but you could be using your router as a bridge.  Let me know.

I'm using direct DHCP.

---

### Post by cameronjcc on 2007-10-10
This is interesting, because you seem to have a network connection, but are unable to perform any advanced networking activities.  Never thought I'd call browsing the internet advanced.  But then again your IM client is quite advanced. Let me think about this one.  Let me know what happens.

---

