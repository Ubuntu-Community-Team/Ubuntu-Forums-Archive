---
title: "Cannot Ping or access Apache over VPN"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by Mark_Larsen on 2015-03-26
All I can ping all internal IP Address, both nics on the Ubuntu Server and pull up pages on apache from inside the local 192.168.0.x network.

I have a remote site connected via VPN 192.168.1.x. From the remote site I can ping all 192.168.0.x address' EXCEPT both nics on the server and apache does not respond. They are just not responding at all. I am hosting a headless VirtualBox on the server and have an ubuntu server running on a VM on the server. THAT hosted machine is responding to pings. So I know the ping is recieved by the server and bridged into the hosted VM and responded to. In If I rdp into a workstation on the 192.168.0.x network I can ping the server from there just fine. 

This is acting like Ubuntu is configured to not respond to requests from other networks. I found on the web [COLOR=#000000][FONT=Courier New]net.ipv4.ip_forward a[/FONT][/COLOR]nd set that to 1. That did not solve the problem. 

I am new to ubuntu and I'm not sure where to start. Any advise would be helpful.

---

