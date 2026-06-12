---
title: "Unable to connect 3 vm together"
date: 2020-02-19
forum: Networking &amp; Wireless
---

### Post by p730 on 2020-02-19
Hi, 
I'm trying to connect 3 virtual machines together, all are ubuntu 18.04,  and I'm having trouble ssh and pinging each of the machines. 
the 3 machines are 
Routers:
network1 : 192.168.100.1 , net2 : 192.168.101.1
client:
192.168.100.2
Server: 
192.168.101.2
all 3 virtual machines are configured using internal network 

when I try pinging the client from router this is what I got: 

[ATTACH=CONFIG]285054[/ATTACH]

and ssh :
[ATTACH=CONFIG]285055[/ATTACH]

I configured the network interface using netplan like this : 
[ATTACH=CONFIG]285056[/ATTACH]

network on client machine: 
[ATTACH=CONFIG]285057[/ATTACH]

I know lots of people are asking this questions but I've tried all of them and It still doesn't work for me.
I also tried allowing firewall for port 80 and even disabled it. 

I'm not sure how to connect these 3 vm togethers.
any help would be appreciated! 
thank you in advance!

---

### Post by TheFu on 2020-02-20
Which hypervisor?  
Using the bridge-utils package with KVM, these NAT connections should work.
For something like virtualbox, probably best to read the networking chapter in that manual.   [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)  Networks aren't connected when they seem to be.

Also, please post text, wrapped in code tags, not images.

---

