---
title: "ssh no route to port 22 -DHCP running thought static"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by gug@fnal.gov on 2008-04-19
Hi,
   This had me going for a while, although I was only spending 1/2 hr a night on it. I was trying to enable sshd to listen on 192.168.25.181 as a static ip address, and but reconfiguring and restarting sshd was saying "no route to port 22". Configured sshd for 127.0.0.1 and it worked fine. I also could not ping to that address. iptables showed no rules, so my initial assumption of a firewall was wrong. I check the routes with netstat and route and that looked fine. What I overlooked was the system came up initially in DHCP mode and not with the static ip I set. D'oh. 
  Changing the network configuration to no use roaming, hence not DHCP, and setting the ip address, subnet mask, and gateway solved the problem. Sometimes the solution is too obvious to notice at first, Just posting in case someone else new to Ubuntu runs into a similar problem.  :)

---

