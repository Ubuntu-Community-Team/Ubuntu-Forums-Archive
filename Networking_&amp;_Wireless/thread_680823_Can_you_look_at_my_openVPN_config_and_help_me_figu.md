---
title: "Can you look at my openVPN config and help me figure out why its not working?"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by jediknight1226 on 2008-01-28
Ok I am new to VPN but here is whats going on...   it shows that I connect to the VPN but I can't access or ping anything. I am running openvpn. My server is running ubuntu and my laptop is running vista. 

My dsl router is set to allow traffic on port 1194. The LAN address of this network is 172.16.0.0 255.255.0.0 

Here is my server config:

> local 172.18.83.171

port 1194

proto udp

dev tun

ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key  

dh /etc/openvpn/keys/dh1024.pem

server 10.19.83.0 255.255.255.0

ifconfig-pool-persist ipp.txt

client-to-client

keepalive 10 120

comp-lzo

persist-key
persist-tun

status openvpn-status.log

verb 3

mute 20

Here is my client Config:

```
client

dev tun

dev-node vpn1226

proto udp

remote 44.x.x.x 1194

route 172.16.0.0 255.255.0.0 vpn_gateway 3

resolv-retry infinite

nobind

persist-key
persist-tun

mute-replay-warnings

ca "C:\\Program Files\\OpenVPN\\easy-rsa\\ca.crt"
cert "C:\\Program Files\\OpenVPN\\easy-rsa\\client.crt"
key "C:\\Program Files\\OpenVPN\\easy-rsa\\client.key"

ns-cert-type server

verb 3

mute 20
```

Both my server and client are using DHCP. I have disabled Windows firewall. I haven't installed a firewall on ubuntu. My dsl router has one but I told it to forward all port 1194 traffic to my server. If you need more info to troubleshoot just let me know.

---

### Post by jediknight1226 on 2008-02-03
awww, come on. surely someone can help?

---

### Post by bartruji on 2008-02-05
Any luck yet? I'm considering OpenVPN. but I may end up using ZeroShell if no other Ubuntu friendly VPNs present themselves.

---

### Post by mveltre on 2008-02-05
is there any route from network 10.19.83.0 (you using for your vpn-clients) to your 'internal' network?

It would help if you could post the output of "route" (as root / with sudo) of both machines (server+connected client) here.

---

