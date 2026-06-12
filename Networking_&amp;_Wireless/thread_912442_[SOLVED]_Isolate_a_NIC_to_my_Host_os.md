---
title: "[SOLVED] Isolate a NIC to my Host o/s"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-09-06
Not sure if this is Networking or Virtualization but here goes:

This is a high-level diagram for project I'm doing:

[[IMG]http://img205.imageshack.us/img205/604/vmue1.th.png[/IMG]](http://img205.imageshack.us/my.php?image=vmue1.png)

I want eth1 to be used by the host o/s (8.04) and the VM's to use eth0 and eth4, respectively.  This way I can still use the campus network and keep the o/s's on the VM's on their own network.

One of the VM's runs a dhcp server, so sometimes it allocates an IP address and other information to my host o/s and I really don't want it to do that.  I want it to allocate that information to the other VM (and other machines on the lab network but that's beside the point).  Each VM is set to the name of the bridged, virtual-to-physical interface per the Virtualbox documentation:

eth0 is bridged to vbox0 and is named br0
eth4 is bridged to vbox1 and is named br1

Here's a copy of my ifconfig:
```

rt3@rt3-desktop:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:0a:5e:54:c0:3a  
          inet6 addr: fe80::20a:5eff:fe54:c03a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65863 (64.3 KB)  TX bytes:12051 (11.7 KB)

br1       Link encap:Ethernet  HWaddr 00:0a:5e:54:c0:14  
          inet addr:10.10.1.3  Bcast:10.10.1.255  Mask:255.255.0.0
          inet6 addr: fe80::20a:5eff:fe54:c014/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25758901 (24.5 MB)  TX bytes:41201 (40.2 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:0a:5e:54:c0:3a  
          inet addr:169.254.5.229  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0a:5e:54:c0:3a  
          inet6 addr: fe80::20a:5eff:fe54:c03a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101364 errors:0 dropped:0 overruns:1 frame:0
          TX packets:1487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28549702 (27.2 MB)  TX bytes:400188 (390.8 KB)
          Interrupt:21 Base address:0x2880 

eth1      Link encap:Ethernet  HWaddr 00:19:d1:7e:4e:84  
          inet addr:136.204.168.136  Bcast:136.204.171.255  Mask:255.255.252.0
          inet6 addr: fe80::219:d1ff:fe7e:4e84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:228101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41094810 (39.1 MB)  TX bytes:33335166 (31.7 MB)
          Base address:0x30c0 Memory:90300000-90320000 

eth4      Link encap:Ethernet  HWaddr 00:0a:5e:54:c0:14  
          inet6 addr: fe80::20a:5eff:fe54:c014/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97424 errors:0 dropped:0 overruns:1 frame:0
          TX packets:877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27602626 (26.3 MB)  TX bytes:95038 (92.8 KB)
          Interrupt:23 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78336 (76.5 KB)  TX bytes:78336 (76.5 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:b5:88:b8:ca  
          inet6 addr: fe80::2ff:b5ff:fe88:b8ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4601 errors:0 dropped:87935 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:66952 (65.3 KB)  TX bytes:1073968 (1.0 MB)

vbox1     Link encap:Ethernet  HWaddr 00:ff:d3:37:28:fe  
          inet6 addr: fe80::2ff:d3ff:fe37:28fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2014 errors:0 dropped:87053 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:176744 (172.6 KB)  TX bytes:191955 (187.4 KB)

rt3@rt3-desktop:~$ 

```

---

### Post by MaindotC on 2008-09-08
Problem solved - props to Sasquatch over at [_Virtualbox Forums_](http://forums.virtualbox.org/viewtopic.php?p=36336#36336).  I escape death yet again!

---

### Post by dcostelloe on 2008-09-27
Hi,
I am trying to run IIS on win 2003 on Virtualbox on Ubuntu :popcorn:
I have followed the bridge link and setup as directed here is my ifconfig results in which my IIS on Virtualbox is listening on port 80 but nothing is getting through. I am using Dynamic DNS also.

ifconfig:

TUNSETIFF: Device or resource busy
device br0 already exists; can't create bridge with the same name
device eth0 is already a member of a bridge; can't enslave it to bridge br0.
There is already a pid file /var/run/dhclient.pid with pid 9545
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/br0/00:1c:c0:10:04:cc
Sending on   LPF/br0/00:1c:c0:10:04:cc
Sending on   Socket/fallback
DHCPREQUEST of 76.64.39.179 on br0 to 255.255.255.255 port 67
DHCPACK of 76.64.39.179 from 76.64.39.178
bound to 76.64.39.179 -- renewal in 233 seconds.
device tap0 is already a member of a bridge; can't enslave it to bridge br0.
david@Bandit:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:1c:c0:10:04:cc  
          inet addr:76.64.39.179  Bcast:76.64.39.183  Mask:255.255.255.248
          inet6 addr: fe80::21c:c0ff:fe10:4cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:205097784 (195.5 MB)  TX bytes:7828358 (7.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:10:04:cc  
          inet6 addr: fe80::21c:c0ff:fe10:4cc/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:217355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:243960930 (232.6 MB)  TX bytes:11618434 (11.0 MB)
          Base address:0xecc0 Memory:dfde0000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104900 (102.4 KB)  TX bytes:104900 (102.4 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:02:05:1d:03  
          inet6 addr: fe80::2ff:2ff:fe05:1d03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46593 errors:0 dropped:55 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1273980 (1.2 MB)  TX bytes:8269913 (7.8 MB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:2a:a7:2f:5b  
          inet6 addr: fe80::2ff:2aff:fea7:2f5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:4993 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vbox1     Link encap:Ethernet  HWaddr 00:ff:db:53:b4:af  
          inet6 addr: fe80::2ff:dbff:fe53:b4af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:4993 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

set Virtualbox from Nat to host and added tap0 in teh setting for network?

Is there something I missed as IIS is not responding to port 80 traffic?

:confused:

---

### Post by MaindotC on 2008-09-27
Just so we're clear, DNS and ports aren't really part of setting up the bridge between the host and virtual interface.  I can help you ensure the interface on your host machine is properly bridged with the virtual interface on the virtual machine.  If that is done correctly, then we can troubleshoot any additional aspects.  

Please post your /etc/network/interfaces file.  If you have a diagram of your set up please post that as well or make up a quick one using Dia.

---

