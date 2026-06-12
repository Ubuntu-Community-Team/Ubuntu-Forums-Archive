---
title: "[SOLVED] OpenVPN Bridged Setup"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by wiseguyxp on 2008-11-26
I am trying to bridge 2 different connections on the same domain.  One goes through a proxy server and screws up a game I'm playing so it can't reach the servers.  I have set up a bridged VPN and the client connects to the server perfectly fine.  I set it to change the default route to go through the VPN and to the other network, where it doesn't have to pass through a proxy.  I can see networked computers and printers on the other network, but I can't access web pages or make new connections outside of the network.  Both networks are actually on the same network, but are separated through NAT.  Here are my config files:

# Server
port 1194
proto tcp
dev tap0
ca keys/ca.crt
cert keys/server.crt
key keys/server.key  # This file should be kept secret
dh keys/dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 10.25.21.212 255.255.255.0 10.25.21.230 10.25.21.239
push "redirect-gateway def1 bypass-dhcp"
client-to-client
duplicate-cn
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
log openvpn.log
verb 3
mute 20

# Client
client
dev tap
dev-node tap0
proto tcp
remote 10.25.21.212 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca "c:\\program files (x86)\\openvpn\\keys\\ca.crt"
cert "c:\\program files (x86)\\openvpn\\keys\\client.crt"
key "c:\\program files (x86)\\openvpn\\keys\\client.key"
ns-cert-type server
comp-lzo
verb 3
mute 20
pull
redirect-gateway

---

### Post by wiseguyxp on 2008-11-26
For anyone in the future with this problem...

I changed /proc/sys/net/ipv4/ip_forward from a 0 to a 1.

I knew it had to be something stupidly simple.

---

