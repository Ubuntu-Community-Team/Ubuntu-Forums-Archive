---
title: "Ipv6 address issue"
date: 2018-07-28
forum: Networking &amp; Wireless
---

### Post by tim162 on 2018-07-28
Ok. I'm new to ubuntu. I use vultr to host vps servers of ubuntu 16.04. I have two possibilities and neither I can get to work so I thought I would ask the pros. 

Scenario 1
I have a server running ipv4 to ssh into. I want to add 4 static ipv6 addresses to it for my masternodes. I can't seem to get this to work 

Scenario 2
They have an ipv6 only server option. I can ssh into it no problem. I put in the command to clone the masternode wallet from github and it errors out on me. I can't get that to work either. 

I'm stuck and have tried searching for everything I can think of. Can anyone lend me a hand. Thanks

---

### Post by Skaperen on 2018-07-29
they are probably using openstack for virtuakization.  all the vps providers i have seen doing openstack + ipv6 have been unable to offer both ipv4 and ipv6 on the same interface.  look around to see if they offer a setup with ipv4 on eth0 and ipv6 on eth1.  or look for another vps provider not using openstack.

---

