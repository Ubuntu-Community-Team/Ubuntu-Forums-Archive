---
title: "need help in openvpn"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by rosegal on 2010-04-12
hi there..

i am connecting openvpn between two pc both running different version of ubuntu...i already do all the configuration and got a new tun interface in my server but could not get it in my client...i start my openvpn in my client and it says "openvpn ok"...still i dont have the connection..

pls anyone help me!!!


this is my openvpn.conf in client

client
dev tun
proto tcp
remote 210.187.x.x 1194
resolv-retry infinite
nobind
user nobody
group nogroup

# Try to preserve some state across restarts.
persist-key
persist-tun
ca /etc/openvpn/ca.crt
cert /etc/openvpn/client1.crt
key /etc/openvpn/client1.key
comp-lzo

# Set log file verbosity.
verb 3

---

