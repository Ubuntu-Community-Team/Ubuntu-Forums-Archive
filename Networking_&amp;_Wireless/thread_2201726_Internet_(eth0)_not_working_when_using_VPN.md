---
title: "Internet (eth0) not working when using VPN"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by klausmcm on 2014-01-25
Hello everyone,

I am losing internet access through my regular ethernet interface (eth0 - assigned static IP of 192.168.1.10 and directly connected to a router) when using OpenVPN. I can still access the internet when using a program that is bound to the OpenVPN interface, tun0. I also have samba shares on this machine which remain accessible to the local network. Local SSH connections also still work but I lose the ability to connect remotely (over the internet) when OpenVPN is up.
My ovpn configuration file looks like this

```
client
dev tun
proto udp
remote ca.privateinternetaccess.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /etc/openvpn/ca.crt
tls-client
remote-cert-tls server
auth-user-pass ./vpnlogin.txt
comp-lzo
verb 1
reneg-sec 0
auth-nocache
```

I was under the impression that 'nobind' would not interfere with any existing network connections.

How do I continue using the VPN and retain internet access with eth0? What am I missing?

---

### Post by tomearp on 2014-01-25
Please paste the output of
```
route
```
Do it with the VPN disconnected, then again with the VPN connected. It sounds likely to be an issue with routing. From a brief look at the [openvpn documentation]("http://openvpn.net/index.php/manuals/427-openvpn-22.html") the nobind option will not influence the routing behaviour of a connection.

If your default route does change when the VPN is connected, with the result that Internet-bound traffic is going over the VPN, then the issue you describe with inbound SSH connections sounds plausible.

The SSH server will see a new connection arriving from a particular IP address and respond back, but the returning packets will go via the VPN. The result will be that the packets arrive back at the machine initiating the SSH connection from the external IP address of the VPN server, and are discarded as unknown.

---

### Post by klausmcm on 2014-01-25
> **tomearp said:**
> Please paste the output of
```
route
```
Do it with the VPN disconnected, then again with the VPN connected. It sounds likely to be an issue with routing. From a brief look at the [openvpn documentation]("http://openvpn.net/index.php/manuals/427-openvpn-22.html") the nobind option will not influence the routing behaviour of a connection.

If your default route does change when the VPN is connected, with the result that Internet-bound traffic is going over the VPN, then the issue you describe with inbound SSH connections sounds plausible.

The SSH server will see a new connection arriving from a particular IP address and respond back, but the returning packets will go via the VPN. The result will be that the packets arrive back at the machine initiating the SSH connection from the external IP address of the VPN server, and are discarded as unknown.

Without OpenVPN
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         unknown         0.0.0.0         UG    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
```

With OpenVPN
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.145.1.5      128.0.0.0       UG    0      0        0 tun0
default         unknown         0.0.0.0         UG    0      0        0 eth0
10.145.1.1      10.145.1.5      255.255.255.255 UGH   0      0        0 tun0
10.145.1.5      *               255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.145.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
198.144.156.55  unknown         255.255.255.255 UGH   0      0        0 eth0
```

Also, whenever I try to run

```
sudo apt-get update
```

the operations times out when OpenVPN is running. I don't understand why that is since I have programs running that do get internet access through the VPN (though I specified the tun interface in their configuration).

---

### Post by tomearp on 2014-01-26
Can you please paste the output of 
```
route -n
```
With the VPN disconnected? Just want to verify whether 'unknown' is the host name of the gateway or if it really is unknown.

Can you also provide some details of the IP structure of the remote network?

---

### Post by klausmcm on 2014-01-26
> **tomearp said:**
> Can you please paste the output of 
```
route -n
```
With the VPN disconnected? Just want to verify whether 'unknown' is the host name of the gateway or if it really is unknown.

Can you also provide some details of the IP structure of the remote network?

Without OpenVPN
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

With OpenVPN
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.144.1.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.144.1.1      10.144.1.5      255.255.255.255 UGH   0      0        0 tun0
10.144.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.144.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
198.144.156.59  192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
```

What do you mean by "remote network"? The network from which I try to access my computer that runs OpenVPN and SSH server? If so, then they change. Sometimes the school network, public hotspots, etc. SSH always worked from any of those networks when OpenVPN was not running though.

---

### Post by tomearp on 2014-01-26
One thing you can try is deleting the first route
```
0.0.0.0         10.144.1.5      128.0.0.0       UG    0      0        0 tun0
```
and the fifth route
```
128.0.0.0       10.144.1.5      128.0.0.0       UG    0      0        0 tun0
```
after the VPN has connected, as these routes will cause Internet-bound traffic to be sent over the VPN.
The first route catches IP addresses in the range 0.0.0.0-127.255.255.255 and the fifth route catches IP addresses in the range 128.0.0.0-255.255.255.255.

If this solves the issue then it will be worth looking at the openvpn documentation for server configuration to see what options are available for giving out routes to clients when they connect.
I'm not particularly familiar with openvpn, so hopefully someone with some better knowledge of setting it up can give some advice!

---

### Post by klausmcm on 2014-01-27
> **tomearp said:**
> One thing you can try is deleting the first route
```
0.0.0.0         10.144.1.5      128.0.0.0       UG    0      0        0 tun0
```
and the fifth route
```
128.0.0.0       10.144.1.5      128.0.0.0       UG    0      0        0 tun0
```
after the VPN has connected, as these routes will cause Internet-bound traffic to be sent over the VPN.
The first route catches IP addresses in the range 0.0.0.0-127.255.255.255 and the fifth route catches IP addresses in the range 128.0.0.0-255.255.255.255.

If this solves the issue then it will be worth looking at the openvpn documentation for server configuration to see what options are available for giving out routes to clients when they connect.
I'm not particularly familiar with openvpn, so hopefully someone with some better knowledge of setting it up can give some advice!

Good news is that I retain my internet access through the default ethernet, eth0, interface.
Bad news is that now my programs using the OpenVPN connection, tun0, no longer send/receive traffic.

This is the current 'route' output (tun0 IP may have changed since a new IP is assigned every time I reconnect)

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.191.1.1      10.191.1.5      255.255.255.255 UGH   0      0        0 tun0
10.191.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
198.144.156.122 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
```

---

### Post by tomearp on 2014-01-27
In order to access the LAN that's at the remote end of the VPN you'll need to add a route.
For example if the remote LAN is 192.168.0.1/24 (192.168.0.1-192.168.0.255) you'd need to use the command:
```
route add -net 192.168.0.0 netmask 255.255.255.0 gw 10.191.1.5 dev tun0
```

Obviously it's tedious to keep having to do this so there must be something in the server config to allow such a route to be automatically handed out when the client connects, without clobbering the client's existing default gateway, especially if the address structure of the virtual interface changes each time.

---

### Post by klausmcm on 2014-01-27
> **tomearp said:**
> In order to access the LAN that's at the remote end of the VPN you'll need to add a route.
For example if the remote LAN is 192.168.0.1/24 (192.168.0.1-192.168.0.255) you'd need to use the command:
```
route add -net 192.168.0.0 netmask 255.255.255.0 gw 10.191.1.5 dev tun0
```

Obviously it's tedious to keep having to do this so there must be something in the server config to allow such a route to be automatically handed out when the client connects, without clobbering the client's existing default gateway, especially if the address structure of the virtual interface changes each time.

Thank you for your help. I will try this later this week. Looks like knowing how to read a routing table would be a good skill to have.

---

### Post by tomearp on 2014-01-28
[This page]("http://www.techrepublic.com/article/understand-the-basics-of-linux-routing/") has some basic info on routing which may be useful.

---

