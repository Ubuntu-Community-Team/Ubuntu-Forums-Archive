---
title: "Setting up machine with 2 interfaces for monitoring traffic"
date: 2016-04-14
forum: Networking &amp; Wireless
---

### Post by Tr2naboy on 2016-04-14
Hi,


I have set up Ubuntu machine (A) which is connected to Cisco 3560 with two interfaces.
- one interface is for monitoring traffic from another server (B)
- another interface is for management and sending traffic to third machine (C).


Second interface is set with static ip. How i should configure the first interface to see the traffic on it?
At the moment I see traffic on switch port sending data to monitoring machine (A) from machine B,  but I can't see any traffic in monitoring machine (A) itself with tcpdump.


Additionally I need to forward the monitored traffic to third machine (C). So I need that from first interface the traffic is sent to second interface in machine A. Please don't suggest to forward data directly to third machine (C) with IPtables, because i need to add additonal headers there.


All the help is very appreciated.

---

### Post by Tr2naboy on 2016-04-16
Now I have found out how i have to configure interface which is listening traffic. I followed this quide [http://www.andrewhay.ca/archives/1144](http://www.andrewhay.ca/archives/1144).

Also I enabled forwarding in kernel with uncommenting net.ipv4.ip_forward = 1 in /etc/sysctl.conf. After that I executed sudo sysctl -p.
Then I added following rules to iptables.
sudo iptables -t nat -A POSTROUTING --outinterface eth1 -j MASQUERADE
sudo iptables -A FORWARD --in-interface eth0 -j ACCEPT.

But still i don't see any effect in sending data to another interface.
Any thoughts?

---

