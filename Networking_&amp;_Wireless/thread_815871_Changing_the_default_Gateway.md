---
title: "Changing the default Gateway"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by germanguy on 2008-06-02
I want to change the default gateway that is detected on the network by my system. There are several networks running at the same time and my computer assigns itself to the wrong gateway. I wanted to know how to change the gateway but still get ubuntu to automatically obtain its ip address. I can get it to use the gateway when setting my ip manually.

Any help is appreciated

---

### Post by SpaceTeddy on 2008-06-02
you need to delete the old gateway and add a new one. This can be done dynamicially after the dhcp-lease was aquired.

To delete a route (in this case the default gw) use this command
```
sudo route del -net 0.0.0.0
```

and then add the gateway you want to use with this command
```
sudo route add default gw %ip
```
where %ip is the ip of ne new gateway.

these changes are temporary, as they will only last until you reboot or a new lease is aquired.

hope it helps :)

---

### Post by peap on 2008-06-02
I have the same problem. Two NICs, both using DHCP and they both work fine but the wrong NIC is used for internet access. 

I can change temporarily with route but I want a permanent, dynamic solution. There must be a simple way to do this and make it stick.

I tried swapping the network cables physically but I get the same result, wrong gateway "first in line".

Running 8.04 server.

---

