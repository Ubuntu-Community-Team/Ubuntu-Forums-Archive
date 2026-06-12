---
title: "Internet no longer works"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by Chosen320 on 2008-08-27
I have the 64bit version of Ubuntu 8.04 installed on my desktop pc.

I also have virtual box setup running Windows Xp with host networking.

Everything has being working fine the last few months until yesterday.

I still have network access. I know this because I can VNC onto my laptop without any problems.

However I have no internet access. I can't ping any addresses.

If I ping google.co.za it resolves the name to 64.233.161.104 but then outputs the following:
```

gareth@chosen:~$ ping google.co.za
PING google.co.za (64.233.161.104) 56(84) bytes of data.
From chosen.local (192.168.1.103) icmp_seq=1 Destination Host Unreachable
From chosen.local (192.168.1.103) icmp_seq=2 Destination Host Unreachable
From chosen.local (192.168.1.103) icmp_seq=3 Destination Host Unreachable

```

In fact networking in my Virtual Box windows XP is also working fine. I can browse the net and connect to a VPN. 

Also my laptop (which I'm using to make this post) is connected to the same switch which in turn is obviously connected to the same router and also runs Ubuntu 8.04

ifconfig outputs the following:
```

br0       Link encap:Ethernet  HWaddr 00:1c:c0:26:bd:3f  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe26:bd3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43721853 (41.6 MB)  TX bytes:26695979 (25.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:26:bd:3f  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe26:bd3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:188472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:46662095 (44.5 MB)  TX bytes:27203754 (25.9 MB)
          Memory:53200000-53220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123344 (120.4 KB)  TX bytes:123344 (120.4 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:35:bc:91:b7  
          inet6 addr: fe80::2ff:35ff:febc:91b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:75916 (74.1 KB)  TX bytes:31309 (30.5 KB)

```


Could the problem be that br0 and eth0 are using the same ip address? If so how do I change this and why did this problem only start yesterday? I've only been using linux for a few months so please step me through anything I need to do.

FYI... every morning I've had to input the following before starting up my virtual machine so that I have internet access in both Ubuntu and Virtual Windows XP.

```

sudo /etc/init.d/networking restart
sudo VboxAddIF vbox0 gareth bro0

```


Thanks in advance.

---

### Post by mellowd on 2008-08-27
What happens if you try and trace to google? How far does it get?

---

### Post by Chosen320 on 2008-08-27
I started following another thread at [https://help.ubuntu.com/community/VirtualBox#8.04%20Hardy](https://help.ubuntu.com/community/VirtualBox#8.04%20Hardy)

It was identical to my setup except in that I added 2 lines to the top of my /etc/network/interfaces file.

It is now
```
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
    bridge_ports eth0

auto lo
iface lo inet loopback
```


ifconfig now generates the following:
```
gareth@chosen:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:1c:c0:26:bd:3f  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe26:bd3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:410169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92072727 (87.8 MB)  TX bytes:58102279 (55.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:26:bd:3f  
          inet6 addr: fe80::21c:c0ff:fe26:bd3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:409380 errors:2 dropped:0 overruns:0 frame:1
          TX packets:397716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:99272468 (94.6 MB)  TX bytes:59580311 (56.8 MB)
          Memory:53200000-53220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136700 (133.4 KB)  TX bytes:136700 (133.4 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:f8:d7:69:45  
          inet6 addr: fe80::2ff:f8ff:fed7:6945/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:35 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

It looks like eth0 is no longer trying to use the same ip as the bridge and now Virtual Box Windows XP is also working fine without me having to put in additional commands.

I've rebooted once and everything seems fine now.

---

