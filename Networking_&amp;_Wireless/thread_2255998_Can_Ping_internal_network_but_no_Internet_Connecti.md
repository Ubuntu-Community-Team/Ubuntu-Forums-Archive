---
title: "Can Ping internal network but no Internet Connection"
date: 2014-12-09
forum: Networking &amp; Wireless
---

### Post by kev9 on 2014-12-09
I have been struggling lately alot with OpenVPN. Have done all kinds of things to fix my OpenVPN connection. Now I am at a stage where my OpenVPN server can be connected to but no internet. I have switched from iptables to ufw just to make things more simplier and to solve this problem. Below are my system outputs:-


Output of UFW
```
Code:
ufw status

Status: active

To                         Action      From
--                         ------      ----
1194/udp                   ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere
Anywhere                   ALLOW       10.8.0.0/16
1194/udp (v6)              ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
443/tcp (v6)               ALLOW       Anywhere (v6)


```





Output of server.conf
```
Code:
port 1194
 proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1"
push "dhcp-option DNS 10.8.0.1"
keepalive 10 120
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
log         openvpn.log
verb 4


```


Output of : /etc/dnsmasq.conf
```
Code:
listen-address=127.0.0.1, 10.8.0.1
bind-interfaces


```
Output of netstat-anup
```
Code:
netstat -anup

root@server02:/home/admin# netstat -anup
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 127.0.0.1:53            0.0.0.0:*                           2287/dnsmasq    
udp        0      0 10.8.0.1:53             0.0.0.0:*                           2287/dnsmasq    
udp        0      0 0.0.0.0:1194            0.0.0.0:*                           2248/openvpn    




```

Output of client.conf 
```
Code:
client
dev tun
proto udp
remote vpn.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /ca.crt
cert /client.crt
key /client.key 
comp-lzo
verb 3
```


I have ipv4 port forwarding turned on too. I still dont understand why there is no traffic. The client does connect to the server but there is no internet. I would really appreciate if someone could advise or help figure out a way to solve this problem. Really appreciate any help.

Thank You 
Kev

---

