---
title: "Problem with VPN with credentials (OpenVPN)"
date: 2019-01-22
forum: Networking &amp; Wireless
---

### Post by sayjan on 2019-01-22
Hi y'all!

I work in a company that just started its IT department, and one of my first tasks was to implement a way to access our internal network from outside. So I set up a machine with an Ubuntu Server 16.04.5 and installed the OpenVPN Server ( Roadwarrior - the lazy way sort of speak...). Now here's the problem - when I create the users they are created without credentials, so it's not very safe. I saw several tutorials on the web and I tried to add the credentials with PAM (adding the lines in server.conf and in the client ovpn config). But when I test it gets stuck in **MANAGEMENT: >STATE:1548165917,WAIT......** and if I wait long enough it gives the TLS handshake failure error:  **TLS key negotiation failed to occur within 60 seconds (check your network connectivity) TLS Error: TLS handshake failed**. But when I delete the lines I added it works no problem!
Can anybody help me? I really need this VPN with credentials...
I leave my configurations here

/etc/openvpn/server.conf

port 1194
proto udp
dev tun
sndbuf 0
rcvbuf 0
ca ca.crt
cert server.crt
key server.key
dh dh.pem
auth SHA512
tls-auth ta.key 0
topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 192.168.X.X"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
cipher AES-256-CBC
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
crl-verify crl.pem
plugin /usr/lib/openvpn/openvpn-auth-pam.so ovpn

client.ovpn

client
auth-user-pass
dev tun
proto udp
sndbuf 0
rcvbuf 0
remote server_IP 1194
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
auth SHA512
cipher AES-256-CBC
setenv opt block-outside-dns
key-direction 1
verb 3

---

