---
title: "iptables redirect traffic"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by sergey.sukhorukov on 2013-12-04
I've tried to redirect traffic from one computer to another through additional computer. 

1  --.>  2  ---> 3

Hosts 2 and 3 have ssh ports opened and ip forwarding are turned on. 
From 1 executing  **ssh <host2>**. As result I need to get in console: "Enter password <host3> root password:"
How to get it?

I have tried on the second host to execute iptables command dor DNAT:
iptables -t nat -A PREROUTING -i eth0 --dport 22 -j DNAT --to-destination <host3>

I've tried to check on host3 if it was any incoming connection on host2 with tcpdump with command: tcpdump host <host2>

After starting ssh on host1 tcpdump returns some info about incoming  connection from host2. But as result on host1 after start ssh command it  is awating and nothing happens. No any errors or text messages! I think  it is wating for an answer from host, but getting it from host3.
How I can to solve the problem?

---

### Post by Lars Noodén on 2013-12-05
> **sergey.sukhorukov said:**
> I've tried to redirect traffic from one computer to another through additional computer. 

Welcome.  Can you describe a little more about what you are trying to do?  If you are trying to forward an SSH connection via an intermediary, that can be done entirely within SSH.

---

### Post by sergey.sukhorukov on 2013-12-05
For now, I'm trying to become familiar with iptables. Just, this problem is more complicated then simple DNAT for opening ports in local network, which has router with NAT. I understand that there must SNAT, but what host is to be set up with SNAT: 1,2,3?

> If you are trying to forward an SSH connection via an intermediary, that can be done entirely within SSH.
Thank you for an advice about SSH. I'll try to explore this method.

---

