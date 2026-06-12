---
title: "Can not ping my other subnet...help"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by mamut0o1 on 2010-08-22
Good Morning; I've been playing around with my routers and I havent figure this out yet. This is my setting:

[DSL]---[voip router:192.168.254.x]-----[Wireless router: 192.168.1.1]

I have two linux boxes @ .254 subnet and I have a wireless laptop on my 192.168.1.X subnet. I can ping my linux box OK. If I'm at 192.168.254.X  I cant ping my other subnet. Could anyone take a shot a this one and help me out....thanks!

---

### Post by cogier on 2010-08-22
A subnet is a not something you can ping. It is a limiter, it restricts the amount of IP addresses you can use. I would expect your subnet mask to be 255.255.254.0. This would allow you to have over 500 computers on your network.

You should be able to ping your computers with 192.168.1.X.

If you look at your router setup you should see something like an "Attached devices" option that will tell you what the IP addresses of the connected computers are.

---

### Post by BinaryEnCoder on 2010-08-22
try changing the subnet to 255.255.0.0 and play a bit with the routing tables, if its not a firewall problem its just matter of routing

---

### Post by BinaryEnCoder on 2010-08-22
> **cogier said:**
> A subnet is a not something you can ping. It is a limiter, it restricts the amount of IP addresses you can use.
you can ping the broadcast .255 ;)

---

### Post by mamut0o1 on 2010-08-22
My fault I was refering to a device on subnet 254. I can ping it from 192.168.1.1 but I can not ping 192.168.1.3 from 192.168.254.4. You are saying I should make the subnet 255.255.254.0?

---

### Post by BinaryEnCoder on 2010-08-22
you should set the subnet mask to 255.255.0.0 and check routing tables @ 1.1

---

