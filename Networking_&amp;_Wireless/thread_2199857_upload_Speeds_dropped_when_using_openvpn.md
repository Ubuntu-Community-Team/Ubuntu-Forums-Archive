---
title: "upload Speeds dropped when using openvpn"
date: 2014-01-16
forum: Networking &amp; Wireless
---

### Post by kaamesh on 2014-01-16
[COLOR=#000000][FONT=Lucida Grande]Hi guys,[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]We have open vpn configured on our firewall . When we do a speedtest (speedtest.net) our download speeds are fine ;9.8 Mbps on a 10 Mbps connection; but our upload speeds are only 0.2Mbps. We tried testing the speed on the wireless network and the upload speeds shoot up to 10-13 Mbps. When a pc is hooked up directly to the router the upload speed increases as well. it only suffers when we try to connect through the firewall. I wonder if openVPN is causing this. Also, on firestarter the tap0 device shows no activity? is this normal?[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]Any Ideas?[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]we use a firestarter firewall[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Interfaces available:-[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande][FONT=Lucida Grande]**Code:**[/FONT]
[COLOR=#006600][FONT=Monaco][B]ifconfig
br0       Link encap:Ethernet  HWaddr 00:15:17:ad:e4:3d  
          inet addr:172.20.20.1  Bcast:172.20.20.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:fead:e43d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:324825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28919110 (28.9 MB)  TX bytes:720617485 (720.6 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:17:ad:e4:3d  
          inet6 addr: fe80::215:17ff:fead:e43d/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:455310123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530091512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47554840139 (47.5 GB)  TX bytes:389381334434 (389.3 GB)
          Memory:b1a00000-b1a20000 

eth1      Link encap:Ethernet  HWaddr 00:15:17:ad:e4:3c  
          inet addr:172.20.21.2  Bcast:172.20.21.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:fead:e43c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:281968822 errors:2 dropped:0 overruns:0 frame:2
          TX packets:201201315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:354715206168 (354.7 GB)  TX bytes:27864072448 (27.8 GB)
          Memory:b1900000-b1920000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2523525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2523525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:365583553 (365.5 MB)  TX bytes:365583553 (365.5 MB)

tap0      Link encap:Ethernet  HWaddr ba:7b:58:aa:6c:42  
          inet6 addr: fe80::b87b:58ff:feaa:6c42/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:11272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:991059 (991.0 KB)  TX bytes:6378820 (6.3 MB)
 [/B][/FONT][/COLOR]
[/FONT][/COLOR]
[B]

[COLOR=#000000][FONT=Lucida Grande]/etc/network/interfaces [/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande][FONT=Lucida Grande]**Code:**[/FONT]
[COLOR=#006600][FONT=Monaco][B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface for our internal network
auto br0
#iface eth1 inet dhcp
iface br0 inet static
address 172.20.20.1
netmask 255.255.255.0
gateway 172.20.20.1
bridge_ports eth0 tap0

# The primary network interface
auto eth1 

iface eth1 inet static
address 172.20.21.2
netmask 255.255.255.0
gateway 172.20.21.3
mtu 9000

auto eth0
iface eth0 inet manual
up ip link set $IFACE up promisc on
down ip link set $IFACE down promisc off

 [/B][/FONT][/COLOR]
[/FONT][/COLOR]
[B]

[COLOR=#000000][FONT=Lucida Grande]openvpn/server.conf [/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande][FONT=Lucida Grande]**Code:**[/FONT]
[COLOR=#006600][FONT=Monaco][B]mode server
tls-server

local 172.20.21.2
port 1194
proto udp

#bridging directive
dev tap0 
up "/etc/openvpn/up.sh br0 tap0 1500"
down "/etc/openvpn/down.sh br0 tap0"

persist-key
persist-tun


#DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 172.20.20.1 255.255.255.0 172.20.20.210 172.20.20.220
push "route 172.20.20.0 255.255.255.0"
push "dhcp-option DNS 172.20.20.1"
push "dhcp-option DOMAIN local"
max-clients 10

#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3
[/B][/FONT][/COLOR]
[/FONT][/COLOR]
[B]

[COLOR=#000000][FONT=Lucida Grande]lemme know if you need any other information about this.. im a complete beginner with only 2 days experience in this so i don'kt know what you would need exactly..[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Thanks for reading it guys/girls ..[/FONT][/COLOR][/B][/B][/B]

---

