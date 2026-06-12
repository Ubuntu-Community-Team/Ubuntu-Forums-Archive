---
title: "VPN trouble, hard life huh."
date: 2016-06-10
forum: Networking &amp; Wireless
---

### Post by cptnrofl on 2016-06-10
Recently, during VPN server configuration the one thing that I've  faced is - I don't have internet access connecting through my VPN  server. Actually I use the VPS(Debian 8 ), where I've installed an VPN.  The client connects normally I've used the trace route command to detect  where traffic stops, and obviously it stops at my VPN server. I really  don't know how to deal with it. Anyone help me please:) Here's my Server  config and Client config. And yes my client side is Windows 7 and 10.

  Server config.

  > port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

  Client config. Note: Server's IP is hidden.

  > client
dev tun
proto udp
remote 107.155.1x4.1x2 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca "C:\\OVPN\\ca.crt"
cert "C:\\OVPN\\client1.crt"
key "C:\\OVPN\\client1.key"
ns-cert-type server
comp-lzo
verb 3

  From client side I tired to test Google's DNS server 8.8.8.8 - still  it doesn't work. I think the problem lies with some of the interfaces on  the server side which break outs to internet. So anyone who suggests  something, just help me with useful advice.

---

