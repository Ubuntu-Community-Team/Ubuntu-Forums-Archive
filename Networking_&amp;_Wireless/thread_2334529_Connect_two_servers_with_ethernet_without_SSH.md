---
title: "Connect two servers with ethernet without SSH"
date: 2016-08-20
forum: Networking &amp; Wireless
---

### Post by YQ002lc2 on 2016-08-20
I have two Ubuntu Servers.
I want to connect the two machines via ethernet. 
I want to be able to view and transfer files between them. 
I would prefer to do this without setting up SSH because these machines will not need to receive remote connections over the internet. 

The machines will connect to the internet for updates... but it is not necessary for what I'm trying to do.

I've viewed [https://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](https://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router) and was able to setup the IPv4 setup and have my machines ping each other, but was not able to connect and transfer files. 

I was able to setup a basic SSH server and use the Nautilus connect to server facility to successfully do what I want to do. But I'm not very savy with ssh setup and would rather not open myself up to unnecessary vulnerabilities associated with insecure ssh servers.


Any ideas of how to set this up securely without SSH? 

Thanks

---

### Post by steeldriver on 2016-08-20
Fundamentally, if two computers can access one another, then **so can any other computer that can establish a route to them**. 

In that sense, it doesn't matter what protocol you use to view and transfer files. For example, you could remove SSH and set up a python simplehttpserver instead - now nobody can access either machine via SSH, but they would potentially be able to via http. Likewise with SAMBA/SMB/CIFS or any other network file sharing protocol.

So unless you run them on an 'air gapped' network (connecting them  directly using an ethernet crossover with link-local addresses, or using  a simple switch in place of a router that is connected to an external  network), SSH is actually your securest option IMHO - since it's designed for exactly that. Beyond that, 


[LIST]
[*]Don't forward any ports on your router
[*]Turn off UPnP
[*]Configure suitable firewalls on the two computers
[*]Disable root SSH access
[*]Use key-based SSH authentication
[/LIST]

---

