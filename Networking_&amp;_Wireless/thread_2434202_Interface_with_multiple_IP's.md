---
title: "Interface with multiple IP's"
date: 2020-01-01
forum: Networking &amp; Wireless
---

### Post by uthall on 2020-01-01
Hello,

I have an Ubuntu 18.04 server which has an interface with two public ips (x and y).

I have a specific external public address that i need to communicate with, but only from ip address x.

How do i specify that only ip x can talk to this external ip?

Thanks

---

### Post by The Cog on 2020-01-01
If x and y are in two different network ranges then just adding a route to the external address via a gateway that is a network neighbour to x should be enough (I think). 

Or this command should work (it's not permanent after a reboot)
```
sudo ip route add $external_address via $gateway src $x_address
```
It's down to you to make sure the return path works, i.e. the external address has a working route back to x. If you pass any NAT routers then the outward and return routes must follow the same path.

---

### Post by SeijiSensei on 2020-01-01
You could also use an iptables OUTPUT rule. Suppose you want to communicate with 10.10.10.10 only from 192.168.1.1.  Then you'd have these rules
```

sudo iptables -A OUTPUT -d 10.10.10.10 -s 192.168.1.1 -j ACCEPT
sudo iptables -A OUTPUT -d 10.10.10.10 -j REJECT

```

---

