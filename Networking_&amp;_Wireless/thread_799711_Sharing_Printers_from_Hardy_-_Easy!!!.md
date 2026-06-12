---
title: "Sharing Printers from Hardy - Easy!!!"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by radamo on 2008-05-19
I am new to linux and am trying to get used to it. One the requirements I have is to be able to share my USB connected printer with windows clients on my home network.  All of the tutorials I located were from older versions and looked way to complicated for what I was trying to do. 

I ran across the best set of instructions in the following "How To" document... [http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/)

Not only good tips on sharing printers but much more as well.  

I hope that others can make good use of it as well. 

Regards,

Rich Adamo

---

### Post by Jordanwb on 2008-05-20
Since I'm in a networking class I found a mistake:

> sudo ufw allow from 192.168.0.0/16 to any port 631

It should actually be

> sudo ufw allow from 192.168.0.0/**24** to any port 631

the network 192.168.0.0 is a Class C address not class B

Also if you don't know if you have a firewall set up: If you installed Ubuntu 8.04 (which I assume is Heron), the ufw firewall is installed by default.

---

### Post by radamo on 2008-05-20
Interesting... I didn't do the firewall steps but sharing my printer worked with my XP laptop.

RA

---

### Post by rumli on 2008-05-21
> **Jordanwb said:**
> 
It should actually be

> 
sudo ufw allow from 192.168.0.0/24 to any port 631 



I don't know much about these things, but [according to Wikipedia]("http://en.wikipedia.org/wiki/Private_network"), it should be 192.168.0.0/16.
Restricting it to 192.168.0.24 would block addresses of the form 192.168.1.xxx which are used by some routers.


> **Jordanwb said:**
> 
Also if you don't know if you have a firewall set up: If you installed Ubuntu 8.04 (which I assume is Heron), the ufw firewall is installed by default.

While ufw does come with 8.04, I don't think it is enabled with any rules by default.  You have to explicitly enable it and add rules yourself.

---

