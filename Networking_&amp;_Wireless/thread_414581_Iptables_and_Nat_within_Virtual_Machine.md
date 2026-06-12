---
title: "Iptables and Nat within Virtual Machine"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by dacky on 2007-04-20
I am attempting to setup two networks, each with separate internet connections, on one physical machine running Ubuntu 6.04 using vmware server, with two separate internet connections (this is to isolate our students from the faculty and staff).  I do not want to run two separate machines at this point. 
Host Machine:  
    Nic 1 (eth0):  Internet  (working)
    Nic 2 (eth1):  Vlan 1 (working)
    Nic 3 (eth2):  Vlan 2 (working)

Virtual Machine:
   Nic 4(eth5):  Bridged to physical card; can connect to Internet with different IP from host (different internet line from above, working within virtual machine fine).
   Nic 5(eth6):  Vlan 3, bridged to physical card;  DHCP from clients works to virtual machine as planned.  But I cannot get Iptables to work to nat Nic 5 to 4, therefore, vlan 3 has no internet connection.

Problem:  Cannot nat or masquerade because every time I try to do something with IPtables in the virtual machine, I get errors, as if IPtables do not work. I keep getting "command not found."  I plan to use a very similar script on the vm as on the host, so writing the firewall script will not be a problem.  

Question:  How can I nat/masquerade two nics in a virtual machine?  I will also need to port forward, but these are all Iptables commands?  Is there something in vmware server that stops iptables from working?  Is there a work around?  Or am I going to be stuck having to buy a new computer just to run the second internet connection (the easiest but most expensive solution)?

I tried to do the same set up (two separate internet connections going into one machine with 2 vlans to one connection and 1 vlan to another connection) with the hosts iptables but could never get two separate internet connections to work.

---

