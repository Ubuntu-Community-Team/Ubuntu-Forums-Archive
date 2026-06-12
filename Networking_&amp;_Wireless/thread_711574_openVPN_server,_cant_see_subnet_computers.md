---
title: "openVPN server, cant see subnet computers"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by ninocass on 2008-02-29
Hi all,

Ive had a look at the other threads on this but i cant seem to find any help.

Ill give some of the details first:

home network 192.168.1.1/24
gateway 192.168.1.254 [BT HOMEHUB ROUTER]
server 192.168.1.50

vpn subnet 10.8.1.0 255.255.255.0


I can connect to the VPN  and access the services running on the server (192.168.1.50) however when i try to connect to any other box on the subnet i cant.

Thanks for any help you can give me

My server.conf
```

 cat /etc/openvpn/server.conf 
#VPN PORT
port 1194

#local Addy
local 192.168.1.50

#Protocol of VPN
proto tcp

#Ethernet
dev tun0

#Key Loc
ca keys/ca.crt
cert keys/server.crt
key keys/server.key 
# Diffie hellman
dh keys/dh1024.pem

#VPN DHCP
server 10.8.1.0 255.255.255.0

#Gateway Push
push "route 192.168.1.0 255.255.255.0"

#VPN Static IP makes sure that a given PKI cert gets the same IP
ifconfig-pool-persist client-addresses.txt

#allow VPN cleints to communicate
client-to-client

#keepalive
keepalive 10 120
#More crypto
cipher AES-128-CBC

#Compression
comp-lzo

#openvpn private after init
user nobody
group nogroup

persist-key
persist-tun

#Status File
status openvpn-status.log

log openvpn

verb 3

mute 20

```

and the client.ovpn

```

cat clients.ovpn 
#Tell this is a client
Client

#Name of VPN copnn
dev-node HomeVPN

#Proto
Proto tcp

#Type of conn
dev tun

#VPN WAN IP
Remote [dynamic DNS address]

#Dealing with keys
persist-key
persist-tun

#Keys
ca ca.crt
cert client.crt
Key client.key

#server crypto
cipher aes-128-cdc

#compression
comp-lzo

verb 3

mute 20

```

ifconfig:
```
dns0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.16.0.2  P-t-P:172.16.0.2  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1024  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:13:8F:ED:E1:DB  
          inet addr:192.168.11.50  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:feed:e1db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:195 (195.0 b)  TX bytes:10283 (10.0 KB)
          Interrupt:20 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1484 (1.4 KB)  TX bytes:1484 (1.4 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.1.1  P-t-P:10.8.1.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1062 (1.0 KB)  TX bytes:5550 (5.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:09:2D:0B  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe09:2d0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1249 errors:5 dropped:0 overruns:0 frame:0
          TX packets:593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160899 (157.1 KB)  TX bytes:82338 (80.4 KB)
          Interrupt:19 Base address:0xe000 

```

ip forwarding
```

cat /proc/sys/net/ipv4/ip_forward
1

```

---

### Post by SpaceTeddy on 2008-03-01
i think what you are missing is information at the receiving end of the connectiong on where to send the replies to. The VPN server knows how to send the packets into your LAN (since it has a nic connected to it) but the clients on the LAN do not know where the VPN is... only the VPN server knows that. So their replies get sent to the default gateway, which should forward them to the internet where they get lost... 

There are three ways i can think of how to solve this...

1,) tell every machine on the LAN that the subnet 10.8.0.0/24 is found at 192.168.1.50. 

2.) tell your networks default gateway where to route packets that are for that subnet, i.e. add a route at the machine having the 192.168.1.254 to route all packets for 10.8.0.0/24 to the ip 192.168.1.50

3.) Masquerade the traffic of the VPN at the VPN server. This means that you will get connecton from the VPN into the local network, But not from the local network to the VPN... since the client on the LAN still don't know where your VPN is...

hope this makes sense... :)

---

### Post by ninocass on 2008-03-04
Thanks for the reply. turned out i had to forward the traffic to the VPN subnet to the openVPN host.  My bthomehub didnt allow that type of forwarding so i had to dig out my old buffalo router.  Working a treat now :D

---

