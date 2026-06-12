---
title: "OpenVPN routing problem"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by zyHEpEJ on 2013-12-21
Hello,


I have a very simple question/problem, but I just couldnt figure out whats wrong. My LAN has the IP range 10.0.0.1-254, where .1 is my router with ISP access. The router connects to a OpenVPN server which has a local lan behind it with the ip range 192.168.1.1-254. The client ip of the VPN connection is 192.168.1.240.


If connected, I can reach (ping) the IPs of the VPN LAN side on the router. But I cannot reach the 192.168.1.0 subnet from my clients behind the router (for example: ping 192.168.1.1 from 10.0.0.2). Heres my routing table from the router:


Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.1.1        0.0.0.0         UG    0      0        0 eth1
10.0.0.0        *               255.255.255.0   U     0      0        0 br-lan
10.0.1.0        *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 tap0


tap0 is the OpenVPN connection. Shouldnt that already work? The OpenVPN server is in bridge mode:


option 'server_bridge' '192.168.1.1 255.255.255.0 192.168.1.240 192.168.1.242'


I already can ping the OpenVPN server itself (192.168.1.1) and all clients on its lan. But just from the router (VPN client), and not from my local lan clients (routing problem).

---

### Post by The Cog on 2013-12-21
Three things come to mind. 

Firstly, is your router configured to do IP forwarding? [http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/)

Secondly, do your other clients know to use your router 10.0.0.1 as their next hop to reach network 192.168.1.0 (or have a default route to 10.0.0.1)? Check the routing tables in your clients.

Thirdly, do the devices on net 192.168.1 know to use 192.168.1.240 as the next hop to reach network 10.0.0.1? When pinging from the router it will use source address 192.168.1.240 unless told otherwise, so being able to ping from the router does not prove the return route net 10 is known at all.

---

### Post by zyHEpEJ on 2013-12-21
Yes of course all clients have their gw set up, the 10.0.0.x clients have 10.0.0.1, and the 192.168.1.x clients 192.168.1.1. IP forwarding of course is enabled. Your third hint I dont understand though. No it wasnt added, I added it just now. You meant this right:

route add -net 10.0.0.0 netmask 255.255.255.0 gw 192.168.1.240

On the OpenVPN server. Ok. I can now ping 10.0.0.1 from the VPN server. But my problem didnt change. I cant ping the 192.168.1.x net from my lan side clients.

---

### Post by The Cog on 2013-12-23
> You meant this right:

route add -net 10.0.0.0 netmask 255.255.255.0 gw 192.168.1.240
Yes, that was what I meant. 

If they all have suitable routes to reach each other, and the router is forwarding packets, it's difficult to imagine what's wrong. On the router, can you try this?
```
ping -i 10.0.0.1 192.168.1.1
``` to see if the bridge knows how to send packets to net 10 properly?

I would probably then start using 
```
tcpdump -n -p -i <ifname> icmp
```
of various machines/interfaces to figure out how far the replies/responses get.

---

### Post by zyHEpEJ on 2013-12-26
Hello,


sorry for my late reply, Christmas time was a bit hectic :( Thanks again for the hints and I got the problem. There was a policy based routing rule I didnt thinkt about, something like this:


iptables -t mangle -A PREROUTING -s 10.0.0.0/24 -j MARK --set-mark 2


And I set anoher one which solved the issue:


iptables -t mangle -A PREROUTING -d 192.168.1.0/24 -j MARK --set-mark 1


But now I have another problem :/ I read myself into why I should use tun instead of tap and not bridging, because it would produce lots of broadcast traffic for example. So I changed my server config to this:


```
config 'openvpn' 'lan'
	option 'enable' '1'
	option 'port' '1194'
	option 'proto' 'udp'
	option 'dev' 'tun2'
	option 'ca' '/etc/easy-rsa/keys/ca.crt'
	option 'cert' '/etc/easy-rsa/keys/server.crt'
	option 'key' '/etc/easy-rsa/keys/server.key'
	option 'dh' '/etc/easy-rsa/keys/dh2048.pem'
	#option 'ifconfig_pool_persist' '/tmp/ipp.txt'
	#option 'ifconfig-pool' '10.8.0.2 10.8.0.10 255.255.255.0'
	option 'keepalive' '10 120'
	option 'comp_lzo' '0'
	option 'persist_key' '1'
	option 'persist_tun' '1'
	option 'status' '/tmp/openvpn-status.log'
	option 'verb' '3'
	#option 'server_bridge' '192.168.1.1 255.255.255.0 192.168.1.200 192.168.1.205'
	option server "10.8.0.0 255.255.255.0"
	list push "route 192.168.1.0 255.255.255.0"
```


But now again I cant get it to work, and it's even worse than before with bridging mode, where in the end I got it to work, but here, I cant.


First confusing thing is that it shows this on the client:




tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255


And on the server:


tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255


Why two adresses for each? and why does the client get 6 (and 5?) and not 2? Also I cant even ping from side to side from the client to the server. My routing table looks a little bit weird too:


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.1.1        0.0.0.0         UG    0      0        0 eth1
10.0.0.0        *               255.255.255.0   U     0      0        0 br-lan
10.0.1.0        *               255.255.255.0   U     0      0        0 eth1
10.8.0.1        10.8.0.5        255.255.255.255 UGH   0      0        0 tun2
10.8.0.5        *               255.255.255.255 UH    0      0        0 tun2
172.20.16.0     *               255.255.248.0   U     0      0        0 tun0
172.20.24.0     *               255.255.248.0   U     0      0        0 tun1
192.168.1.0     10.8.0.5        255.255.255.0   UG    0      0        0 tun2


And on the server:


Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         188-194-*-* 0.0.0.0         UG    0      0        0 eth1
10.0.0.0        *               255.255.255.0   U     0      0        0 tun2
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun2
172.20.24.0     *               255.255.248.0   U     0      0        0 tun1
172.20.24.0     *               255.255.248.0   U     0      0        0 tun0
188.194.190.0   *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 br-lan

---

