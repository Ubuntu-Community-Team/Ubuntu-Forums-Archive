---
title: "OpenVPN and bridging"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by cookie200 on 2007-02-09
Good morning!  First off thank you for glancing over my thread.  I have a small problem that is making my head scratch.  I am playing around with openvpn and have routing down.  Now i wanted to set up the bridging portion on a different machine just to learn.


So some background on my network

VPN Eth0: 10.250.250.106
Lan: 10.250.250.0 255.255.255.0
VPN: 10.250.25.0 255.255.255.0 
WAN: Cox 
The machine is an old computer just for testing, as soon as i get it working i was gonna move it to a faster machine. (Linux vpntest 2.6.15-27-server #1 SMP Fri Dec 8 18:43:54 UTC 2006 i686 GNU/Linux)

Here is a bit of my config files

Server.conf

port 1194
local 10.250.250.106
proto udp
dev tap0
ca keys/ca.crt
cert keys/server.crt
key keys/server.key #secret file
dh keys/dh1024.pem
server-bridge 10.250.25.2  255.255.255.0 10.250.25.200 10.250.25.210


and my here is my bridge-start config  (im using the one from openvpn site)

br="br0"
tap="tap0"
eth="eth0"
eth_ip="10.250.250.106"
eth_netmask="255.255.255.0"
eth_broadcast="10.250.250.255"

I do have bridge-utilities installed.  Before i enabled the bridge-start script everything works.  I can ping websites and all that fun stuff.  I run ./bridge-start  and this is what i get

> root@vpntest:/etc/openvpn# ./bridge-start-test
Thu Feb  8 23:21:02 2007 TUN/TAP device tap0 opened
Thu Feb  8 23:21:02 2007 Persist state set to: ON


Great!  But here lies the problem.  I cant ping any websites at all (yes i have the DNS settings in the resolv.conf)  I can still access the internal network as i can ssh into box and ping the gateway.  So im not sure if im doing something right with the bridge, or maybe im missing something?

Here is what my ifconfig looks like after starting the bridge.  

> br0       Link encap:Ethernet  HWaddr 00:08:C7:57:22:72
          inet addr:10.250.250.106  Bcast:10.250.250.255  Mask:255.255.255.0
          inet6 addr: fe80::208:c7ff:fe57:2272/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6694828 (6.3 MiB)  TX bytes:9436988 (8.9 MiB)

eth0      Link encap:Ethernet  HWaddr 00:08:C7:57:22:72
          inet6 addr: fe80::208:c7ff:fe57:2272/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:87590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8133131 (7.7 MiB)  TX bytes:9621287 (9.1 MiB)

tap0      Link encap:Ethernet  HWaddr 06:9D:87:38:AF:B9
          inet6 addr: fe80::49d:87ff:fe38:afb9/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20722 errors:0 dropped:19 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:46110 (45.0 KiB)  TX bytes:3249905 (3.0 MiB)



Before i start the bride eth0 has the 10.250.250.106 address

Thank you for reading this over, im sure it is something im missing that is really simple.

---

### Post by cookie200 on 2007-02-09
Just an update

i was reading around and i ran the command route add default gw 10.250.250.1

> Fri Feb  9 10:30:51 2007 TUN/TAP device tap0 opened
Fri Feb  9 10:30:51 2007 Persist state set to: ON
root@vpntest:/etc/openvpn# ping google.com
ping: unknown host google.com
root@vpntest:/etc/openvpn# route add default gw 10.250.250.1
root@vpntest:/etc/openvpn# ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=239 time=32.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=238 time=32.0 ms


:guitar: 

Gonna test it out tonight when i get home 8-) 8-) 8-)   Hopefully that is all i needed to do!

---

### Post by cookie200 on 2007-02-09
Okay so i got it working. As i stated earlier 

here is what i did for others who happen to run into this problem

I guess i misread some info on the openvpn site.

Either way at the part where i have

> server-bridge 10.250.25.2 255.255.255.0 10.250.25.200 10.250.25.210

So i thought the vpn should have its own subnet, i guess i was wrong.  Since my LAN is 10.250.250.x i changed it from above to:

> server-bridge 10.250.250.X 255.255.255.0 10.250.250.0 10.250.250.x

X = unused ip addresses on my LAN

and it worked!  :KS 

Just an FYI !

---

