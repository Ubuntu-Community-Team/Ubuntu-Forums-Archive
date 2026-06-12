---
title: "Cannot ping to client network from server side"
date: 2017-03-14
forum: Networking &amp; Wireless
---

### Post by baveux on 2017-03-14
Hi OpenVPN Team,


I have installed OpenVPN to establish a Site to Site connection between two remotes networks


Here my Network schema


[[IMG]http://zupimages.net/up/17/11/m4h2.jpg[/IMG]]("http://zupimages.net/viewer.php?id=17/11/m4h2.jpg")


So I can ping the client side (192.168.209.0/24) to the server side (10.101.0.0/16) => OK
I can ping from the client side to 10.8.0.1 (server) => OK
And I can ping from the server side to 10.8.0.6 (client ) => OK


But I **can't** ping from server side to client network 


For example from the server to the client machine => ping to 192.168.209.2 => Doesn't work


I enabled echo "1"> /proc/sys/net/ipv4/ip_forward


**_SERVER :_**


Here my server.conf


```
port 1194
proto tcp
dev tun
ca keys/ca.crt
cert keys/xxx.crt
key keys/xxx.key 
dh keys/dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
log         openvpn.log
verb 3

```


ip route


```
10.8.0.0/24 via 10.8.0.2 dev tun0 
10.8.0.2 dev tun0  proto kernel  scope link  src 10.8.0.1 
192.168.209.0/24 via 10.8.0.1 dev tun0 
```




iptables -t nat -v -L


```
Chain POSTROUTING (policy ACCEPT 150 packets, 23401 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   32  2664 MASQUERADE  all  --  any    enp0s25  10.8.0.0/24          anywhere  
```


**_CLIENT_**


client.conf


```
client
dev tun
proto tcp
remote xxxxxx 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
remote-cert-tls server
comp-lzo
verb 3
```


ip route




```
10.8.0.1 via 10.8.0.5 dev tun0
10.8.0.5 dev tun0  proto kernel  scope link  src 10.8.0.6
10.101.0.0/16 via 10.8.0.6 dev tun0

```


iptables 




```
Chain POSTROUTING (policy ACCEPT 31 packets, 2653 bytes)
 pkts bytes target     prot opt in     out     source               destination
    3   252 MASQUERADE  all  --  any    tun0    192.168.209.0/24     anywhere
    0     0 MASQUERADE  all  --  any    ens4    10.101.0.0/16        anywhere
    0     0 MASQUERADE  all  --  any    ens4    10.8.0.0/24          anywhere
```




When I'm on the server and i ping the client with tunnel IP 10.8.0.6


Here's the result with tcpdump on tun0


on the server
```
02:18:47.922486 IP 10.8.0.1 > 10.8.0.6: ICMP echo request, id 7110, seq 39, length 64
02:18:47.934675 IP 10.8.0.6 > 10.8.0.1: ICMP echo reply, id 7110, seq 39, length 64
```


on the client
```
02:20:05.004943 IP 10.8.0.1 > 10.8.0.6: ICMP echo request, id 7110, seq 116, length 64
02:20:05.004980 IP 10.8.0.6 > 10.8.0.1: ICMP echo reply, id 7110, seq 116, length 64
```


So it is ok it works


But When I'm on the server and I ping the client with his IP LAN 192.168.209.2


Here's the result with tcpdump on tun0


on the server


```
02:21:26.057201 IP 10.8.0.1 > 192.168.209.2: ICMP echo request, id 7114, seq 7, length 64
02:21:27.057172 IP 10.8.0.1 > 192.168.209.2: ICMP echo request, id 7114, seq 8, length 64
```


But Nothing on the client


It's the same when I'm make a ping trough the tunnel


like ping -I tun0 192.168.209.5, notthing append on the client side 


How is it possible ?  Can you help me please


Thank you in advance

---

### Post by QIII on 2017-03-14
Hello!

Are you expecting an answer from an OpenVPN developer?

---

### Post by SeijiSensei on 2017-03-14
```
192.168.209.0/24 via 10.8.0.1 dev tun0
```

This routing won't work.  The gateway to the 192.168.209.0/24 network is 10.8.0.6.  So delete that route and replace it with:
```
sudo ip route add 192.168.209.0/24 via 10.8.0.6
```

Also I'd turn off the masquerading rules until you get the rest of this sorted out.  This is a simple routing problem and doesn't require NAT.

Any better?

---

### Post by baveux on 2017-03-15
Thank you for your reply

So I deleted all the iptables rules

I tried to add the route on the server but I have an error

[HTML]sudo ip route add 192.168.209.0/24 via 10.8.0.6
RTNETLINK answers: Network is unreachable[/HTML]

---

### Post by SeijiSensei on 2017-03-15
OK, let's start over.

**Hosts on 10.101.0.0/16** should have 10.101.0.159 as their default gateway.

```

sudo ip route add default via 10.101.0.159

```

The **server at 10.101.0.159** should have a route to the 10.8.0.0/24 network via the tunnel, and a route to the 192.168.209.0/24 network via 10.8.0.6 as I described before.

```

sudo ip route 10.8.0.0/24 dev tun0
sudo ip route 192.168.209.0/24 via 10.8.0.6

```

The **server at 10.8.0.6** needs a route to the 10.101.0.0/16 network via the tunnel:
```

sudo ip route 10.8.0.0/24 dev tun0
sudo ip route 10.101.0.0/16 via 10.8.0.1

```

**Machines in 192.168.209.0/24** need a default route via 192.168.209.2
```
sudo ip route add default via 192.168.209.2
```

Now machines behind both the servers will forward all traffic through those machines, and they should know where to send it.

OpenVPN may set up routing for the 10.8.0.0/24 network, but you'll need static routes for 192.168.209.0/24 and 10.101.0.0/16.

---

