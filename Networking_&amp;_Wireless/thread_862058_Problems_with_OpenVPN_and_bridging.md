---
title: "Problems with OpenVPN and bridging"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by iler on 2008-07-17
Hi!

I have tried to setup VPN tunnel with OpenVPN at my homeserver but with little success. I can get my vpn-client (windows xp with openvpn) to connect to my server with vpn and it even gets ip address from my internal dhcp-server (it's visible in tcpdump -i tap0). But when I try to ping some server in my internal network from my vpn-client it just says "Request timed out" and nothing is going on in tcpdump -i tap0. I have also opened port 1194 and added iptables rules for br0 and tap0 as suggested in openvpn.net howto.

```
# Allow TAP interface connections to be forwarded through other interfaces
$IPT -A FORWARD -i tap0 -j ACCEPT
$IPT -A FORWARD -i br0 -j ACCEPT
$IPT -A FORWARD -i br0 -o $LAN -j ACCEPT
$IPT -A FORWARD -i $LAN -o br0 -j ACCEPT

# Allow TAP interface connections to OpenVPN server
$IPT -A INPUT -i tap0 -j ACCEPT
$IPT -A INPUT -i br0 -j ACCEPT


```

Here is some info from my system:

```

# netstat -arn

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 br0
83.145.211.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         83.145.211.254  0.0.0.0         UG        0 0          0 eth0

# brctl show

bridge name	bridge id		STP enabled	interfaces
br0		8000.0011deaebeef	no		eth1
							tap0

```

And here are my configs:

```
**server.conf**

port 1194
proto udp
dev tap0
mode server
ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/i28.crt
key /etc/openvpn/easy-rsa/keys/i28.key
dh /etc/openvpn/easy-rsa/keys/dh2048.pem
keepalive 10 120
cipher AES-256-CBC
comp-lzo
daemon
push "redirect-gateway local def1"
max-clients 100
user nobody
group nobody
persist-key
persist-tun
status /var/log/openvpn-status.log
log /var/log/openvpn.log
verb 3


**client.conf**

client
dev tap
proto udp
remote i28.fi 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
cipher AES-256-CBC
comp-lzo
verb 3
redirect-gateway def1
ns-cert-type server

```

And here is my script to start the bridge:

```
#!/bin/bash

#################################
# Set up Ethernet bridge on Linux
# Requires: bridge-utils
#################################

# Define Bridge Interface
br="br0"

# Define list of TAP interfaces to be bridged,
# for example tap="tap0 tap1 tap2".
tap="tap0"

# Define physical ethernet interface to be bridged
# with TAP interface(s) above.
eth="eth1"
eth_ip="192.168.1.7"
eth_netmask="255.255.255.0"
eth_broadcast="192.168.1.255"
gw="83.145.211.254"

for t in $tap; do
    openvpn --mktun --dev $t
done

brctl addbr $br
brctl addif $br $eth

for t in $tap; do
    brctl addif $br $t
done

for t in $tap; do
    ifconfig $t 0.0.0.0 promisc up
done

ifconfig $eth 0.0.0.0 promisc up

ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast

```

So could anyone help me so I could get my vpn-tunnel to work?

---

### Post by iler on 2008-07-21
So am I alone with this kind of problem :)?

---

### Post by someone13 on 2008-07-21
No, your not alone with the problem.  Whenever I try to run the bridge-start script I get a /dev/tap0 not found.

Nice.

---

### Post by mooseman089 on 2008-08-10
Hey, I think I had the same problem has you when I ran the bridge-start but I fixed it by modifiying the script to add a route add default gw. It seems like your script asks for the gateway but never uses it so try this one
```
#!/bin/bash

#################################
# Set up Ethernet bridge on Linux
# Requires: bridge-utils
#################################

# Define Bridge Interface
br="br0"

# Define list of TAP interfaces to be bridged,
# for example tap="tap0 tap1 tap2".
tap="tap0"

# Define physical ethernet interface to be bridged
# with TAP interface(s) above.
eth="eth0"
eth_ip="192.168.1.185"
eth_netmask="255.255.255.0"
eth_broadcast="192.168.1.255"
gw="192.168.1.1"

for t in $tap; do
    openvpn --mktun --dev $t
done

brctl addbr $br
brctl addif $br $eth

for t in $tap; do
    brctl addif $br $t
done

for t in $tap; do
    ifconfig $t 0.0.0.0 promisc up
done

ifconfig $eth 0.0.0.0 promisc up

ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast
route add default gw $gw
```
I'm also having have the problem with getting the /dev/tap0 not found but I can't seem to find a solution for it yet.

---

### Post by iler on 2008-08-10
Thanks for the reply but I got it already working :) I will post my solution later on.

---

### Post by mooseman089 on 2008-08-10
That would be great.  I see to have the tun and bridge module running but when I run openvpn --mktun --dev tap0 I do not see the tap0 device in /dev

---

### Post by iler on 2008-08-17
Here is what I did to get openvpn work in Hardy 8.04. I have tested connecting from couple of Windows XP computers and it works fine for me.

For creating br0 I inserted this into /etc/network/interfaces
eth1 is my LAN interface not WAN

```

auto br0
iface br0 inet static
        address 192.168.1.7
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
pre-up openvpn --mktun --dev tap0
bridge_ports eth1 tap0

```

This is my server.conf

```

port 1194
proto udp
dev tap0
mode server
tls-server
ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh2048.pem
keepalive 10 120
cipher AES-256-CBC
comp-lzo
daemon
push "redirect-gateway local def1"
max-clients 100
user nobody
group nobody
persist-key
persist-tun
status /var/log/openvpn-status.log
log /var/log/openvpn.log
verb 3

```

And this is my client.conf (for windows)

```

proto udp
dev tap
client
remote host_address 1194
cipher AES-256-CBC
comp-lzo
ns-cert-type server
redirect-gateway def1
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
ping 60
ping-exit 180
ping-timer-rem
verb 3

```

Everything else should be kinda trivial, just follow openvpn.net tutorial and remember to open correct ports and services in your firewall config.

---

