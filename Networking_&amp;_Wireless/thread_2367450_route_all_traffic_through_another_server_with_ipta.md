---
title: "route all traffic through another server with iptables?"
date: 2017-07-30
forum: Networking &amp; Wireless
---

### Post by arya6000 on 2017-07-30
Let's say I have 2 servers

Server A and Server B

I want all traffic from server B to pass through Server A, I understand one way to do this is by using a VPN server on Server A. But as far as I know there is a way to do this by using iptables which will be very reliable.

How can this be achieved by using iptables?

---

### Post by SeijiSensei on 2017-07-30
You don't need anything like iptables for this.  Just make server B's default route point to A.  If A is 192.168.0.1 and B is 192.168.0.2, you'd use this on server B:
```

sudo ip route del default
sudo ip route add default via 192.168.0.1

```
Now if server B is actually a router, with additional clients behind it, then you need some additional routing rules.  But lets start with the easy stuff first.

---

### Post by arya6000 on 2017-07-30
> **SeijiSensei said:**
> You don't need anything like iptables for this.  Just make server B's default route point to A.  If A is 192.168.0.1 and B is 192.168.0.2, you'd use this on server B:
```

sudo ip route del default
sudo ip route add default via 192.168.0.1

```
Now if server B is actually a router, with additional clients behind it, then you need some additional routing rules.  But lets start with the easy stuff first.

The machines are in different subnets. One is from Linode and another one is my local machine. Would your method work with my scenario?

---

### Post by SeijiSensei on 2017-07-31
That's a bit more complicated.  Here's one method you might try.

1)  Install OpenVPN on both machines and [set up a shared-key static tunnel]("http://openvpn.net/static.html") between them.

2)  On the Linode, add a route for the other server's network subnet using that server's VPN address.

3)  On the local server set its default gateway to use the Linode's VPN address.

Suppose your tunnel has 10.1.1.1 on the Linode and 10.1.1.2 on the local server.  Also let the local server be in the 192.168.1.0/24 subnet. You'd could add these routes:
```

# on the Linode
sudo ip route add 192.168.1.0/24 via 10.1.1.2

# on the local server
sudo ip route del default
sudo ip route add default via 10.1.1.1

```
Now the Linode knows where to send traffic for the server's network, and the server sends all its outbound traffic upstream to the Linode over the tunnel.

Sadly there's just one teensy problem.  How do you send the VPN packets to the Linode's public address?  With just the routes above, all your traffic ("default") goes to the VPN address including, unfortunately, the traffic you need to send to the Linode to maintain the tunnel.  To solve this you need one more route that sends traffic to the Linode's address via your local router out to the public Internet.  Suppose the Linode has address 10.10.10.10.  You need one more route on the local server like this:
```

# local server - send VPN traffic via local router not tunnel
sudo ip route add 10.10.10.10 via 192.168.1.1

```
assuming 192.168.1.1 is the router for the 192.168.1.0/24 network that the server inhabits.  Now traffic for 10.10.10.10 goes over the Internet, and everything else goes through the tunnel.

You don't need to send all the traffic over the tunnel if all you want to do is let the servers exchange data.  Then all you need is the tunnel.  You'd point applications on the local server to the Linode's 10.1.1.1 address.  If that's all you want, then you can omit the stuff about changing the default gateway.

---

