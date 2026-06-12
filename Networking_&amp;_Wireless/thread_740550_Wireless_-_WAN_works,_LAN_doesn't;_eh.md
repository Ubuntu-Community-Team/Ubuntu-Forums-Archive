---
title: "Wireless - WAN works, LAN doesn't; eh??"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by intermod on 2008-03-30
I have a sony laptop (new), Gutsy 7.10 with Intel 3945ABG (ipw3945 driver) wireless on-board.  I can ping URLs (its resolving) and have good web access.  However, I cannot ping any other LAN devices (windows, Linux, anything) except the laptop itself.

Laptop also has WinXP (dual boot) and the 3945abg wireless works flawlessly.

In Gutsy I have tried Orinoco, Cisco and Senao pcmcia 802.11b cards - all worked great for a while, but now they don't.

My firewall/router (Linux RH9) serves DHCP 192.168.0.100-254; 192.168.0.2-99 static range; the 3945 is set for dynamic and gets an IP address in the correct subnet (192.168.0.220).  

Connection Information NetworkManager indicates:

IP addr: 192.168.0.220
bc 192.168.0.255
SNM: 255.255.255.0
Def Route: 192.168.0.1
Pri DNS: 192.168.0.1
Sec DNS: 68.87.78.130

Ping to the gateway:

greg@greg-laptop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.29 icmp_seq=1 Destination Host Unreachable
From 192.168.0.29 icmp_seq=2 Destination Host Unreachable
From 192.168.0.29 icmp_seq=3 Destination Host Unreachable

192.168.0.29 is Ethenet interface which is unplugged, and unchecked.  

Pings elsewhere result in the same.

When I delete the 68.87 SEC DNS, I lose name resolution, so their seems to be an issue with the firewall's ability to pass name requests to the WAN (but using only 192.168.0.1 in WinXP works...). This has me really stumped.  I am running bind and named in the firewall.

Any ideas?  

intermod

---

### Post by intermod on 2008-03-30
It is now working - not exactly clear why.  

When the 3945 was inoperative on the LAN, and I had no ethernet connection - even when Ethernet was "unchecked" in NM, I had found the following

greg@greg-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

So a ping to 192... would first go out eth0? and fail?  Just now, I unchecked Ethernet in NM, then edited 

sudo vim /etc/network/interfaces

and eliminated the line 

auto eth0

While the auto eth0 reappeared when I rebooted, I *think* Ethernet remained unchecked in NM; so now I get:

greg@greg-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1

eth1 is the 3945.  I can only guess that the earlier ping was going out on the Ethernet and failing; and all LAN calls would as well.   Never got to eth1.  

Likely problem:  There seems to be no way to disable Ethernet in Network Manager when I am using wireless, unless I do bunch of manual edits.  How do disable eth0 when I am wireless?  

intermod

---

