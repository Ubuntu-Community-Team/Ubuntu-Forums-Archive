---
title: "Connect to connected OpenVPN client from different subnet"
date: 2017-07-14
forum: Networking &amp; Wireless
---

### Post by fatgeek on 2017-07-14
I have a machine running Xubuntu 17.04 that is connected as a client to a VPN via OpenVPN (2.3.11). When I have the client connected, I can access the machine remotely via SSH and VNC if I am on the same subnet (my LAN subnet, 192.168.1.0/24). I can not access it from my wireless subnet, 192.168.2.1/24. If I disconnect from OpenVPN I can connect from the wireless subnet. I do not have access to the server to make config changes as this is a paid VPN service. Is there a way to allow the incoming connection from multiple subnets while OpenVPN is running?

---

### Post by jamapii on 2017-08-04
So I think there is some routing missing. The client should have a route within openvpn, that tells 192.168.2/24 is reachable through openvpn. I think a server directive 

push "route ..."

should help. If not, put

route ...

directly in the client config

---

