---
title: "Open VPN client not allowing internet connection"
date: 2016-02-23
forum: Networking &amp; Wireless
---

### Post by adamjay78gmail.co on 2016-02-23
I use an ubuntu server 14.04 openvpn client to connect to mystaticip.com.  When I connect to them, I do not have access to internet. I show nameserver 8.8.8.8 under /etc/resolv.conf. Here is my ip route below.

 0.0.0.0/1 via 172.16.72.1 dev tun0default via 192.168.0.1 dev eth0
128.0.0.0/1 via 172.16.72.1 dev tun0
172.16.72.0/23 dev tun0  proto kernel  scope link  src 172.16.72.104
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.30
208.100.194.45 via 192.168.0.1 dev eth0

client.conf

setenv FORWARD_COMPATIBLE 1
client
server-poll-timeout 4
nobind
remote static.tunnelservers.net 1194 udp
remote static.tunnelservers.net 1194 udp
remote static.tunnelservers.net 443 tcp
remote static.tunnelservers.net 1194 udp
remote static.tunnelservers.net 1194 udp
remote static.tunnelservers.net 1194 udp
remote static.tunnelservers.net 1194 udp
remote static.tunnelservers.net 1194 udp
dev tun
dev-type tun
ns-cert-type server
reneg-sec 604800
sndbuf 100000
rcvbuf 100000
#redirect-gateway def1
#up /etc/openvpn/update-resolv-conf
#down /etc/openvpn/update-resolv-conf
#route add 192.168.0.0 mask 255.255.255.0 gw 192.168.0.25
# NOTE: LZO commands are pushed by the Access Server at connect time.
# NOTE: The below line doesn't disable LZO.
comp-lzo no
verb 3
setenv PUSH_PEER_INFO

---

