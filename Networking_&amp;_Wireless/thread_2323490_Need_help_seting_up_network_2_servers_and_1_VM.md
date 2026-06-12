---
title: "Need help seting up network 2 servers and 1 VM"
date: 2016-05-05
forum: Networking &amp; Wireless
---

### Post by Miguel_Gomez on 2016-05-05
Hello guys,

i am facing some difficulties creating some iptables rules. I would appreciate some help

So this is the diagram. I have 2 servers and one VM. On server 1 i have 2 public ips. I use the main for the server itself but the second one is free. On server 2 i have just one ip. I want the VM to have public IP so basically I want to route all traffic from 1.1.1.2 to vm machine(4.4.4.5) on server2. So for example if i open putty and give address 1.1.1.2 port 22 i am logging directly to 4.4.4.5 port 22. On the other side i want 4.4.4.5 to route to 1.1.1.2 and then to internet. The idea being VM1 to operate with 1.1.1.2 as if it is its own IP. I would appreciate some help with the iptables rules. Thanks[IMG]http://i.imgur.com/OS6UHnt.jpg[/IMG]

---

