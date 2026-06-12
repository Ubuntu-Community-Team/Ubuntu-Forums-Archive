---
title: "I can't find the  openvpn-status.log"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by bigboy7foru on 2009-09-17
Is there a certain place it would have put it?
 
I searched the whole computer and no luck.
 
Do I need to make a path for it if so how do i go about doing that?

---

### Post by bigboy7foru on 2009-09-17
```
mode sever
tls-server

local 192.168.0.100
port 1194 ## default openvpn port
proto udp

#bridging directive
dev tap0
up "/ect/openvpn/up.sh br0"
down "/ect/openvpn/down.sh br0"

persist-key
persist-tun

#certificates and encryption
ca ca.crt
cert server.crt
key server.key # This file should be kept secret
dh dh1024.pem
tls-auth ta.key 0 # This file is secret

cipher BF-CBC # Blowfish (default)
comp-lzo

#DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 192.168.0.100 255.255.255.0 192.168.0.150 192.168.1.159
push "dhcp-option DNS 192.168.0.4"
push "dhcp-option DOMAIN tech.diamondvoice.net"
max-clients 10

#log and security
user nobody
group nogroup
keepalive 10 123
status openvpn-status.log <this is what im trying to find not sure if i need to create it or what?>
verb 3

```

---

### Post by Zyprexa on 2009-11-22
i found mine in ~

---

