---
title: "Setting up Routes"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by ouellettem on 2008-05-29
I am on a network with two different subnets. I am connected to a internal private 10.111.0.0 255.255.0.0 network and I have network equipment that are on a different subnet 25.111.0.0. I have a static ip on the 10.111.0.0 and I can communicate no problem within this subnet but I want to be able to also communicate with the other subnet 25.111.0.0 network so I can use network software to see the switches and such. I can do this on my pc with XP but I am struggling to make it work on Ubuntu. I have on nic card. 

Thanks, Mark

---

### Post by elamericano on 2008-05-29
You'll need a second ip address on this new subnet. When you add that, your route should be added automatically.

Try this:
sudo ifconfig eth0:1 25.111.0.222 netmask 255.255.0.0

I've guessed that you're using eth0 and that 25.111.0.222 is available on your network.

---

