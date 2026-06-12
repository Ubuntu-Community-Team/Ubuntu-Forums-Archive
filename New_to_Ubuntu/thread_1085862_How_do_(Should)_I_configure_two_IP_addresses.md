---
title: "How do (Should) I configure two IP addresses"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by davbran on 2009-03-03
I recently went to ssh into my box and was unable to connect. It seems that after adding vmware to my install, I was unable to connect to SSH. I had to call my roommate and walk him through removing eth0 from dhcp to static so I could connect. This worked fine, but when I got home I found I had no internet. so I deduced that I didn't have nameservers set up. I finally set those up and had internet again. The trouble is, only one of my nics activates, and I can no longer access internet on my vmware now because of this. Or so it seems.

Does inet in "iface eth0 inet static" stand for internet?

If so, should I set up the second nic for local and if so, how?

this is my interfaces set up

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.113
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

auto eth1
iface eth1 inet static
        address 192.168.0.66
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1


ifconfig returns the following

eth0      Link encap:Ethernet  HWaddr 00:1d:60:be:7a:f0
          inet addr:192.168.0.113  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:febe:7af0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14803 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
          RX bytes:15996990 (15.9 MB)  TX bytes:2107611 (2.1 MB)
          Interrupt:246 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1266200 (1.2 MB)  TX bytes:1266200 (1.2 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:172.16.199.1  Bcast:172.16.199.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:192.168.251.1  Bcast:192.168.251.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by ibuclaw on 2009-03-03
Firstly, about eth1 missing, try:
```
sudo ifconfig eth1 up
```

Secondly, the network module **vmnet8** is on a completely different network to your network card, so perhaps this is the reason why it can't access it?

Regards
Iain

---

### Post by davbran on 2009-03-03
When I 

```
sudo ifconfig eth1 up
```

I lose eth0, sorry I should have added that to my original post.

---

