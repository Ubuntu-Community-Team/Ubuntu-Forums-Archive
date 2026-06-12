---
title: "NIC Bonding: Does not failover successfully. Only one NIC is active"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by Akhran on 2006-10-25
I have bonded two NICs by 

1) installing ifenslave package
2) adding the 'bonding' module into /etc/modules
3) creating a /etc/modprobe.d/bond0 file and with the content "options bonding mode=0 miimon=100"
4) edit /etc/network/interfaces by removing all references to eth0 and eth1 and adding bond0 configuration
5) reboot

This method works on one of my machines with lots of other stuff already installed. However, on my refresh installation, it does not work; when eth0 is disabled, the connectivity is down. It doesn't failover to eth1. But if eth1 is disabled, the connectivity stays up. Looks like only eth0 is active.

Configuration as follows:

# cat /etc/modules

loop
bonding

# cat /etc/modprobe.d/bond0

options bonding mode=0 miimon=100

# cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
	address 192.168.1.220
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.254
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.254
	dns-search home.intranet
	up ifenslave bond0 eth0 eth1
	down ifenslave -d bond0 eth0 eth1

# ifconfig

bond0     Link encap:Ethernet  HWaddr 00:0C:29:B8:02:DC  
          inet addr:192.168.1.220  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feb8:2dc/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8644 (8.4 KiB)  TX bytes:4442 (4.3 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0C:29:B8:02:DC  
          inet6 addr: fe80::20c:29ff:feb8:2dc/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5686 (5.5 KiB)  TX bytes:1630 (1.5 KiB)
          Interrupt:169 Base address:0x1400 

eth1      Link encap:Ethernet  HWaddr 00:0C:29:B8:02:DC  
          inet6 addr: fe80::20c:29ff:feb8:2dc/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2958 (2.8 KiB)  TX bytes:2812 (2.7 KiB)
          Interrupt:177 Base address:0x1480 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

# cat /proc/net/bonding/bond0

Ethernet Channel Bonding Driver: v3.0.3 (March 23, 2006)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: eth0
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:0c:29:b8:02:dc

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:0c:29:b8:02:e6

Appreciate any help on this.

Thanks !

---

### Post by mips on 2006-10-25
Have a look at [http://www.ubuntuforums.org/showthread.php?t=99668](http://www.ubuntuforums.org/showthread.php?t=99668) and compare.

---

### Post by Akhran on 2006-10-25
Before posting my first post, I did a search on 'bonding' and read Ubusole's post. Tried out his method, but I got the same result as the method I used.

Thanks though :)

> **mips said:**
> Have a look at [http://www.ubuntuforums.org/showthread.php?t=99668](http://www.ubuntuforums.org/showthread.php?t=99668) and compare.

---

