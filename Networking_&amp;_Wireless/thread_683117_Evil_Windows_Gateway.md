---
title: "Evil Windows Gateway"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by lusth on 2008-01-30
OK, I'm having a networking problem that I suspect is not my fault (it never is).

I have a server (HP DL580 G2) running ubuntu 7.10 (gutsy) server. It is on the
network with a static IP of 130.160.47.82 and a domain name of beastie.cs.ua.edu.
I can ssh and connect to this server from any machine on 130.160.47.*. I can also ssh
to this machine from my home and from a machine out of state. What I can't
do is ssh to beastie from my desktop machine which is on 130.160.46.*, but I can
ssh to the out-of-state machine and then from there get to beastie.

My desktop machine has as a gateway a machine on the 46 network.When I run
traceroute beastie.cs.ua.edu, I get to the gateway and nothing beyond.  The
gateway is a windows machine and the windows guys say it's my problem. It
doesn't seem to be a problem with my desktop since I can ping other windows
machines on 47. So the problem must be with beastie or with the gateway.

On beastie:

% sudo iptables -L 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

No firewall running, right?

Is there anyway I can demonstrate unequivocally which machine has the problem?

Thanks,

john

---

