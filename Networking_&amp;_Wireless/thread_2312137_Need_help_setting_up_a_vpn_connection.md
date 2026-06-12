---
title: "Need help setting up a vpn connection"
date: 2016-02-02
forum: Networking &amp; Wireless
---

### Post by James Wilde on 2016-02-02
Running 14-04.  I have loaded network-manager-openvpn.  I have four .ovpn files in /etc/openvpn plus a ca.crt file.  Here are the results of several tests I make:

```
me@mybox:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 eth0
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
me@mybox:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.20.193    0.0.0.0         UG        0 0          0 tun0
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.10.20.192    0.0.0.0         255.255.255.192 U         0 0          0 tun0
78.110.166.50   10.0.2.2        255.255.255.255 UGH       0 0          0 eth0
me@mybox:~$ traceroute 78.110.166.50
traceroute to 78.110.166.50 (78.110.166.50), 64 hops max
  1   10.0.2.2  0,177ms  0,003ms  0,003ms 
  2   *  *  * 
  3   *  *  * 
  4   *  *  * 
  5   *  *  * 
  6   *  *  * 
^C
me@mybox:~$ ping dn.se
ping: unknown host dn.se
me@mybox:~$ 

```

The first section shows two routes, default and details of the local network.  My machine has an IP of 10.0.2.15.

The second section shows routes after the vpn is started.  As I read it, the default route goes via a gateway, 10.10.20.193.  My local network is reached via the default, which seems strange, in fact impossible since the 10 net is a private network.  It appears that the tunnel network is also reached via the default gateway, with similar comments to above on the local network.  Finally, the remote server is reached via the gateway to my local network, even more remarkable.

The third section shows the result of trying to ping the remote server, which bombed out after reaching my local gateway, not surprisingly. and the fourth section indicates that I have no reachable dns.

I would have expected a routing table roughly as follows:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.20.193    0.0.0.0         UG        0 0          0 tun0
10.0.2.0        10.0.2.2         255.255.255.0   U         0 0          0 eth0
10.10.20.192    10.10.20.193         255.255.255.192 U         0 0          0 tun0
78.110.166.50   10.10.20.193        255.255.255.255 UGH       0 0          0 eth0



```

In fact the last line would be superfluous inasmuch as the default route goes via 10.10.20.193.

And then there's the question which dns server I would use.  Can I assume that my vpn supplier has a dns server on the remote vpn server or at least reference to one there?

Any comments?  Am I way off track?  And if not, I have to find some way to completely rewrite the routing table when I start the vpn.  Not my idea of fun at all.

---

### Post by SeijiSensei on 2016-02-02
The client must maintain a connection via the public Internet to the VPN server so it can exchange the tunnel traffic.  So you have a route to the VPN server via your usual IP gateway, and all other traffic goes through the tunnel to the server as the default gateway.  If the route for 78.110.166.50 also went through the tunnel as you suggest, there would be no way for the encapsulated traffic to reach the server.

I don't think you need to rewrite the routes at all.  Can you not ping external addresses via the tunnel?

The VPN provider should have all the information you need on things like DNS.  If you use a public server like Google's 8.8.8.8, the DNS queries would go through the tunnel and then resent to Google.

---

### Post by James Wilde on 2016-02-02
Thanks for your reply, SeijiSensei.

No, I can't ping external addresses via the tunnel, that's it.  In the example I provided in the op I tried to ping dn.se, a local newspaper, but the address couldn't be resolved.

And how about lines two and three in the second netstat in the op?  It appears to me that the route to the local network and the route to the tunnel network both go through the default route where the gateway is an address on the tunnel, but the local network and the tunnel network both use private addresses.  With the routing table as it is I can't even ping the tunnel gateway, 10.10.20.193.  I would have thought at least the second line should have 10.0.2.2 as the gateway to the 10.0.2.0 net.

---

