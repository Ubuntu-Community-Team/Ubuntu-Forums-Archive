---
title: "Network switching"
date: 2018-11-07
forum: Networking &amp; Wireless
---

### Post by markrazorx on 2018-11-07
Is there a way to switch between Wireless and Wired connections **without** switching either of the connections **off** when both are **connected**?

I am using 18.04.

---

### Post by mitesh.agrwl on 2018-11-08
Hi,

> Is there a way to switch between Wireless and Wired connections **without** switching either of the connections **off** when both are **connected**?

You can use the metric or flags for this purpose. 

```
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0b1
link-local      *               255.255.0.0     U     1000   0        0 wlp2s0b1
192.168.1.0     *               255.255.255.0   U     600    0        0 wlp2s0b1

```

if you have more than one interface connected to the network they will show up in here. 

Another way is to use a firewall, GUFW provides a GUI interface.
```

$ sudo apt install gufw
```

Regards,
Mitesh

---

### Post by slickymaster on 2018-11-08
Thread moved to **Networking & Wireless** for a better fit

---

### Post by 1clue on 2018-11-08
Haven't really done it before, but if the system is not a router I'd try to delete the default route and add a different one.

That said, you'll likely have static routes defined on both interfaces, assuming there are other networks attached to each.

In my understanding normally you wouldn't mess with it. The networking stack should get the "cost" of sending packets to a certain address and then choose the best route each time.

---

### Post by The Cog on 2018-11-09
I think 1clue is right. Changing your default route is probably what you are looking for. Either delete one of your existing default routes (you probably already have one for each interface). 
Better still, just add a new default route with a lower metric (lower metric = more preferred) than the existing routes e.g.:
```
sudo ip route add default via 192.168.0.254 dev wlp2s0  proto static  metric 10
```

---

