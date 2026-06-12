---
title: "Can't ping or SSH to machine from LAN, only WAN"
date: 2015-07-26
forum: Networking &amp; Wireless
---

### Post by David_Picella on 2015-07-26
I have a Ubuntu 14.04 machine on AWS that seems to be working fine but I can only access the server from the WAN (public) IP and not the LAN (private) IP

I have other servers on the same LAN subnet so I am pretty sure that the hardware is all working, and I am sure that the machine binds to the correct subnet IP when it boots.

In fact, I can ping the machine on the LAN subnet and it will ping just fine on the loopback but if I try to ping or SSH the machine from another machine on the private LAN subnet there is no response.  My security group is allowing inbound traffic for all ICMP on 0.0.0.0/0 (all ports) and SSH port 22 from 0.0.0.0/0 ...

Can't figure out why this machine does not like my private LAN?  Any assistance or thoughts about how to solve this would be much appreciated!

---

### Post by Lars Noodén on 2015-07-27
Welcome.

Is the packet filter (iptables with or without UFW) allowing access on the LAN address?

Is SSH configured to allow access?  Specifically does sshd_config have anything for ListenAddress set?

---

