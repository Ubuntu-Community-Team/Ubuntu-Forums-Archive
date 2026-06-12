---
title: "connect to a router on a remote client side through OpenVPN"
date: 2017-08-30
forum: Networking &amp; Wireless
---

### Post by kandresen on 2017-08-30
I have an OpenVPN server on my VPN server which all offices connect to. All offices have dynamic IP addresses from their respective Internet provider.  
I got an office "A" with an IP range 192.168.20.1/24 (my laptop is usually here with permanent OpenVPN IP 10.15.0.10)
I got an office "B" with an IP range 192.168.1.1/24 (remote client system is here with permanent OpenVPN IP 10.15.0.14)

When I need to access for instance the router in office B I have so far used Unix sockets as such: 

ssh -D <local_socket_port> -f -C -q -N <username>@10.15.0.14
And then changing the socks5 setup of Firefox to visit for example the router setup. 

This has been working quite ok when such as Firefox, however, can I skip the socks5 tunnel with a route configuration instead?  

I have tried for instance: 
ip route add 192.168.1.0/24 via 10.15.0.14   # --> Network is unreachable

---

### Post by SeijiSensei on 2017-08-30
Have you enabled packet forwarding on both machines by setting 
```
net.ipv4.ip_forward=1
```
in /etc/sysctl.conf?  Ubuntu, like most modern distros, will not forward packets across interfaces by default as a security measure.

---

### Post by kandresen on 2017-08-31
That seem to be the default value: 
> cat /proc/sys/net/ipv4/ip_forward
1

That was the result on both the client machines and the server.

---

