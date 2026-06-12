---
title: "Bridge Needed?"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by otterit on 2013-11-10
Do I need to change to CLI? Does this need a bridge setup to allow cross communication between the two subnets?

Configuration: 

Eth1: 10.2.1.1 -- 255.255.255.0 -- 10.2.1.1
Laptop1: 10.2.1.10-- 255.255.255.0 -- 10.2.1.1
Ping Eth1 to Laptop1: **Successful**
Ping Laptop1 to Eth1: **Successful**

Eth1: 10.3.1.1 -- 255.255.255.0 -- 10.3.1.1
Laptop1: 10.3.1.10-- 255.255.255.0 -- 10.3.1.1
Ping Eth2 to Laptop2: **Successful**
Ping Laptop2 to Eth2: **Successful**

Ping Laptop2 to to Eth1: **Successful** (Ping across NICs)
Ping Laptop1 to Eth2: **Successful** (Ping across NICs)

Ping Laptop1 to Laptop2: **FAIL**
Ping Laptop2 to Laptop1: **FAIL**

Everything is currently configured in the GUI (Network Manager). (Using crossover cables directly connected between devices.)

---

### Post by iLikeStrongJava on 2013-11-10
For starters, I'm not clear on what you're trying to do?  You have two machines connected with a crossover cable?  What happens when you ping 127.0.0.1 on each?

---

### Post by The Cog on 2013-11-10
Since the laptops are able to ping the opposite NICs, the routing tables in the laptops must be OK -  they have routes to the other network. My guess is that you haven't configured the Ubuntu in the middle to forward packets. This web page says it all: [http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/)

---

### Post by otterit on 2013-11-10
The Cog:  

SOLVED. Thank you!

---

