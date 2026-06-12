---
title: "Problem with pushing all traffic through vpn server"
date: 2016-02-09
forum: Networking &amp; Wireless
---

### Post by crs2 on 2016-02-09
I set up openvpn server on one VM and client on the other. I can  establish connection and ping eachother but when i try to route all  traffic through vpn i cant. My browser will keep loading and loading but  nothing happens.

my server conf 

```
dev tun
proto udp
port 17003
user nobody
group nogroup
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
ca ca.crt
cert server.crt
key server.key
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
persist-key
persist-tun
client-cert-not-required
plugin /usr/lib/openvpn/openvpn-plugin-auth-pam.so login
verb 4
```

and client

```

dev tun
proto udp
port 17003
user nobody
group nogroup
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
ca ca.crt
cert server.crt
key server.key
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
persist-key
persist-tun
client-cert-not-required
plugin /usr/lib/openvpn/openvpn-plugin-auth-pam.so login
verb 4
```

on server i set

```

ip_forward=1
DEFAULT_FORWARD_POLICY="ACCEPT"
```

and add this in before.rules

```

# START OPENVPN RULES
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0]
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE
COMMIT
# END OPENVPN RULES

```


is there anything else i should do to make this work?

---

### Post by SeijiSensei on 2016-02-09
You need to add a route on the client to the VPN server via your gateway router.  The client needs to see the server directly so it can send the encapsulated traffic over the tunnel.  

Suppose the VPN server's public address is 10.10.10.10, and your gateway router is 192.168.1.1.  Try adding a route similar to this:
```
sudo ip route add 10.10.10.10 via 192.168.1.1
```

---

### Post by crs2 on 2016-02-10
my internal network is 10.80.0.0/24 and my VPN is 10.8.0.0/24. Should i set route to internal adress or vpn through gateway?

---

### Post by SeijiSensei on 2016-02-10
You need a route to the specific IP address of the VPN server.  I used the private address 10.10.10.10 for that in my example, but obviously unless you're testing this out in a laboratory situation, the VPN server will have a publicly-accessible Internet address.  The routing table needs an entry for the server like I gave above.  The default gateway should be the upstream VPN address, probably something like 10.8.0.1 or 10.8.0.2.

---

### Post by crs2 on 2016-02-11
How can i check my server public ip? Whats the point of setting route to openvpn server through my gateway? I thought i can send my traffic by tun connection that i have already established.

---

### Post by SeijiSensei on 2016-02-11
How can you connect to the VPN server if you don't know its address or hostname?  If you know the hostname, but not the address, run the command "host server.example.com" with the server's name to get its address.

I'll try answering your second question one more time.  A VPN consists of encapsulated traffic that is encrypted and sent to the server upstream.  In order for the traffic to reach the server there needs to be a connection between the two machines via the public Internet.  All the other traffic can go through the tunnel, but the two machines need to communicate directly to pass the tunnel traffic back and forth.

---

### Post by crs2 on 2016-02-11
> How can you connect to the VPN server if you don't know its address or hostname?
I know server ip in my internal network, and that ip is set in server config file. i can ping through the tunnel but i cant send any traffic

> In order for the traffic to reach the server there needs to be a connection between the two machines via the public Internet.
My server and client are in the same network. I thought i can do this without internet just using my local connection. Connect form client to server using local and then connect to internet. Is it possible?

---

### Post by SeijiSensei on 2016-02-11
You still need a route to the server that exists outside the tunnel.  It doesn't matter where the machines are located.

---

