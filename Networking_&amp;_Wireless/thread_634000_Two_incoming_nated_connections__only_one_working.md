---
title: "Two incoming nated connections / only one working"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by gavrochelegnou on 2007-12-07
Hello, 

I have an ubuntu server with two network cards, each one connected to a router, each router connected to Internet.
Each router have a NAT rule that forwards the HTTP (80) port to this ubuntu box.
But only one at a time is working.
If my eth0 has a gateway 192.168.2.1 , then all incoming traffic from eth0 is working
If my eth1 has a gateway 192.168.3.1 then all traffic from eth1 is working
but can't get the two incoming connections to work at the same time .

Any Idea ?

---

### Post by mpokrywka on 2007-12-07
This doesn't work because if both interfaces are up, then only one default route (to internet) will be active.
You can solve this problem by adding special routing rules:
```
sudo bash
```

Add additional routing table names to /etc/iproute2/rt_tables
```
echo "100 internet-for-eth0" >> /etc/iproute2/rt_tables
echo "101 internet-for-eth1" >> /etc/iproute2/rt_tables
```

add routes to defined routing tables:
```
ip route add default via 192.168.2.1 table internet-for-eth0
ip route add default via 192.168.3.1 table internet-for-eth1
```

now add routing rules that will force packets to go through proper interface:
```
ip rule add from 192.168.2.123 lookup internet-for-eth0 pref 1000
ip rule add from 192.168.3.222 lookup internet-for-eth1 pref 1001
```

Change those 2.123, 3.222 addresses to your proper addresses on eth0 and eth1

---

