---
title: "Setting up a second network"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by rgorby on 2008-06-05
Here is my setup

1 Windows Machine

4 Ubuntu 7.10 Machines

I want to have two separate networks, 1 100/Mbps network going thru my wireless router (192.168.1.1, which works fine), and one gigabit network going thru my gigabit switch for file transfers.  Ubuntu machines are using eth0 for 100/Mpbs network and eth1 for gigabit. I believe I have the routing setup properly.  

```

# ip route show

192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.106 

10.10.10.0/24 dev eth1  proto kernel  scope link  src 10.10.10.106 

169.254.0.0/16 dev eth0  scope link  metric 1000 

default via 192.168.1.1 dev eth0 

default via 10.10.10.106 dev eth1  scope link  metric 100 

default via 192.168.1.1 dev eth0  metric 100 

```

This is where I am having the problem, I guess I need to route my gigabit traffice thru a computer on the gigabit network, which I chose to be 10.10.10.106.  What needs to be installed and setup on this machine to get this to work, I need to route traffic between my machines to use eth1, all machines use a static ip don't know if that would help.  I chose to do it this way because I was having trouble getting gigabit speeds having the switch connected to my router and need my laptop to also be able to connect to all machines.

---

### Post by rgorby on 2008-06-05
Here is some more information.

Eth0 will connect all machines to the Internet thru a wireless router and allow communication with a XP laptop.  Eth1 will be gigabit, won't be connected to the Internet (or router) and will be used for internal traffic.  I guess all I need is to be able to route to certain machines using eth1 and and get Internet and route to laptop with eth0.  Attached is a table of what I mean.

---

