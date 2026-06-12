---
title: "OpenVPN behind gateway, after connection cannot access LAN Network"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by wpsd-office on 2014-07-14
Hi I'm planning to deploy openvpn to my server. This is my network

My PC ------> Router -------> OpenVPN Server [192.168.0.5 gw 192.168.0.1] and other PC connected to Router
                                        OpenVPN Addres [192.168.160.0/24]

My PC [ IP 192.168.1.3 gw 192.168.1.254 ]
Router[ WAN 192.168.1.200 LAN 192.168.0.1 ]

OpenVPN Server have only one NIC, for easy scalability I'm planning to use "route" instead of "bridging"

Here is my openvpn server configuration :

local 192.168.0.5
port 1194
proto udp
dev tap0
ca ' ...pem'
cert '... pem'
key '... pem'
dh 'dh1024.pem'
server 192.168.160.0 255.255.255.0
keepalive 10 120
comp-lzo
user nobody
group nobody
persist-key
persist-tun
verb 3
mute 20
push "route 192.168.0.0 255.255.255.0"
push "route 192.168.160.0 255.255.255.0"

Here is my client conf

client
dev t
proto udp
remote xxx.xxx.xxx.xxx 1194
float
remote-random
resolv-retry infinite
nobind
persist-key
persist-tun
ca '... pem'
cert '... pem'
key '... pem'
comp-lzo
verb 3
explicit-exit-notify 3
mute 20

I can connect to the Server flawlesly using openvpn.

This is my route table after connecting
Destination     |Gateway         |Genmask         |Flags |Metric| Ref|    Use| Iface
0.0.0.0             | 192.168.1.254   |0.0.0.0         |UG    |0|      0|        0| wlan0
192.168.0.0      | 192.168.160.1|   255.255.255.0   |UG    |0|      0|        0| tap0
192.168.1.0      | 0.0.0.0            |255.255.255.0   |U     |9|      0|        0 |wlan0
192.168.160.0  | 0.0.0.0           |255.255.255.0|   U     |0|      0|        0 |tap0



currently I open firewall to allow all, enable ip4_forward from /etc/syctl.conf.
have forward option in the iptables
iptable -t nat -A POSTROUTING -s 192.168.160.0/24 -o eth0 -j MASQUERADE

problem is I cannot access to any other PC on the LAN 192.168.0.0/24
ping to 192.168.160.1 also not working

I doubt that something wrong with the routing table, but no idea where to fix.

Can anyone help me ? I'm frustrated with this thing....

---

### Post by SeijiSensei on 2014-07-14
Why are you masquerading traffic for 192.168.160.0/24 via eth0?  The routing table says it should be using tap0.  Moreover I don't see any eth0 interface in the routing table, just tap0 and wlan0.

---

