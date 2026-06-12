---
title: "[Ubuntu Server] OpenVPN and routing tables..."
date: 2014-10-16
forum: Networking &amp; Wireless
---

### Post by lemaitre2 on 2014-10-16
Hi,

I'm using an OpenVPN server (rev 2.3.2) to manage an ESXi Server.
The problem is, when I want to create a VM using a local (where the OVPN server is at) ISO, it goes through my VPN, to the PC used for management and back to the ESXi server.
The upload link between the OVPN server and client is very slow, so any operation like that take hours, and I can't disconnect my OVPN client, otherwise the ISO will be disconnected as well.

Here's my OVPN server config file:

> mode server
proto tcp
port xxx
dev tun


ca ca.crt
cert *.crt
key *.key
dh *.pem

key-direction 0
cipher AES-256-CBC

server 10.8.0.0 255.255.255.0
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS x.x.x.x"
push "dhcp-option DNS x.x.x.x"

user nobody
group nogroup
chroot /etc/openvpn/jail
persist-key
persist-tun
comp-lzo

verb 5
mute 20
status openvpn-status.log




How can I solve this issue?

Thank you.

---

